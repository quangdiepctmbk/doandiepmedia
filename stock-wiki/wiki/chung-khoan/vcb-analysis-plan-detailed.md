# Kế hoạch phân tích VCB — Chi tiết từng bước

## Phase 1: Data Engineering
> **Mục đích:** Xây dựng feature matrix sạch, chuẩn hóa, backtest-ready cho VCB

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu ML4T |
|------|----------|---------------|-----------------|
| 1.1 | **Download OHLCV VCB (HOSE: VCB)** từ 2010 → nay. Lấy daily close, open, high, low, volume. Nguồn: Cafef / SSI / VNDirect / yfinance (nếu có VN ticker) | CSV/Parquet: date, open, high, low, close, volume. Check split-adjusted | Ch8: price-volume data |
| 1.2 | **Download VN-Index + VN30** cùng kỳ, cùng format | 2 series benchmark | Ch2: financial data universe |
| 1.3 | **Download báo cáo tài chính quarterly** — EPS, BVPS, ROE, NIM, NPL, CAR, P/E, P/B. Quarterly từ 2010. Nguồn: Cafef / SSI | 1 row/quarter, forward-filled to daily. Lưu point-in-time. | Ch8: fundamental features |
| 1.4 | **Download macro data** hàng tháng: lãi suất NHNN (refinancing, discount, OMO rate), CPI (% YoY), credit growth, PMI, USD/VND. Nguồn: SBV, GSO, Bloomberg | Series weekly/daily — interpolate monthly to daily, forward-looking bị cấm | Ch25 FX features pattern |
| 1.5 | **Xây feature matrix tổng hợp** — merge tất cả lên daily timestamp. Forward-fill fundamental/macro. | 1 file Parquet `vcb_features.parquet`: date + 40–70 feature columns + target columns (NaN ở tương lai) | — |
| 1.6 | **Thêm target columns** — forward return 5d, 21d, 63d. Dùng `.shift(-N)` tính return từ close → future close | 3 target columns (fwd_ret_5d, _21d, _63d). NaN cho N rows cuối mỗi horizon | Ch7, Ch11: label engineering |

**Yêu cầu:** (a) Không dùng future data làm feature. (b) Lưu raw và processed riêng. (c) Ghi chép provenance: ngày crawl, source, bất thường.

---

## Phase 2: Feature Validation + Baseline Models
> **Mục đích:** Kiểm tra feature nào có predictive power; thiết lập OOS validation framework + baseline benchmark

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 2.1 | **IC test từng feature** — Spearman rank correlation giữa feature tại t và forward return 21d. Tính hàng năm: mean IC, ICIR, positive-fold share | Bảng feature × year: IC, ICIR, %positive. Highlight feature nào stable sign. | Ch20 NB03 |
| 2.2 | **FDR control** — tính t-stat từng feature vs forward return. Multiple-testing correction (Benjamini-Hochberg). Threshold q=0.05. | Danh sách feature "significant" (reject H0) vs "failed" | Ch6, Ch7: multiple testing |
| 2.3 | **Correlation matrix** giữa các feature — loại redundant (pair correlation > 0.9). Giữ feature có IC cao hơn. | Feature set giảm còn 20–40 features | Ch8: feature dedup |
| 2.4 | **Baseline OLS** — walk-forward: train 2010–2016, test 2017, roll forward yearly. Predict forward return 21d. | Bảng: date, pred, actual. Tính IC test-set, hit rate @top20% | Ch11: OLS pipeline |
| 2.5 | **Baseline Ridge (α=10² → 10⁶)** — walk-forward same window. Grid search α on validation fold. Lưu best α mỗi window. | IC test-set (Ridge) so sánh vs OLS. Ridge thường thắng. | Ch11: regularized regression |
| 2.6 | **Baseline Naive** — 2 benchmarks: (a) Buy & Hold VCB, (b) Inverse volatility (equal vol-weighted banking basket). | Daily equity curves, Sharpe, max drawdown. Cần để sau ở Phase 4. | Ch16: backtest baseline |
| 2.7 | **IC decay plot** — vẽ IC trung bình rolling 252d. Feature nào IC dương ổn định? Feature nào mất power theo thời gian? | Plot + diagnosis. Feature survival ≠ strategy survival giai đoạn này. | Ch20 NB03 |

**Yêu cầu:** (a) OLS/Ridge dùng deterministic seed. (b) Lưu kết quả vào MLflow-style CSV: training_runs, prediction_sets. (c) Phase 2 kết thúc có danh sách shortlisted features.

---

## Phase 3: Primary Modeling
> **Mục đích:** XGBoost/LightGBM với walk-forward, hyperparameter optimization, interpretability

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 3.1 | **XGBoost walk-forward** — train 2010–2016, predict 2017, expand yearly. Mặc định parameters. | pred vs actual test-set mỗi window. IC, hit rate. | Ch12: GBM |
| 3.2 | **Optuna HPO** trên 1 validation fold (2018). Search space: n_estimators, max_depth, learning_rate, subsample, colsample_bytree, reg_alpha, reg_lambda. 100 trials. | Best params. Feature importance (gain, cover, weight). | Ch12 NB03 |
| 3.3 | **LightGBM walk-forward** — replicate 3.1 + 3.2 với LGB. So sánh vs XGB. | IC, hit rate, training time, feature importance. Chọn 1 model hoặc ensemble. | Ch12 NB03 |
| 3.4 | **TreeSHAP** — lấy model best của XGB/LGB, tính SHAP values cho test-set mỗi window. | SHAP summary plot, feature ranking theo mean|SHAP|. Feature nào stable qua windows? | Ch12 TreeSHAP |
| 3.5 | **Conformal Prediction** — tính prediction intervals cho test-set. Dùng CP với alpha=0.1 → 90% interval. | % coverage (lý tưởng ~90%). Interval width theo regime. | Ch11 NB07, Ch12 NB10 |
| 3.6 | **Model selection** — so sánh OLS, Ridge, XGB, LGB, ensemble. Chọn model(s) best theo IC + hit rate + Sharpe (nếu đã backtest). | Decision matrix. Model registry: model artifact + metadata. | Ch26 NB06 (MLflow pattern) |
| 3.7 | **CatBoost optional** — thử CatBoost nếu XGB/LGB yếu. Ordered boosting xử lý categorical sector features. | Bổ sung nếu cần. | Ch12 NB04 |

**Yêu cầu:** (a) So sánh đúng window — không cherry-pick. (b) SHAP output phải interpretable (feature A ảnh hưởng thế nào tới VCB). (c) Conformal intervals cho uncertainty quantification.

---

## Phase 4: Causal + Factor Analysis
> **Mục đích:** Trả lời "feature X có causal effect lên VCB, hay chỉ correlation?"

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 4.1 | **Double Machine Learning** — chọn candidate causal features: lãi suất NHNN, credit growth, NPL. Y = VCB return 21d, D = candidate, X = các control features còn lại. | ATE estimate + confidence interval. Nếu CI chứa 0 → không reject null. | Ch15 NB02–NB05 |
| 4.2 | **BSTS Event Study** — discrete events: NHNN rate decision dates, TTCK crash (2020 COVID, 2022 VN-Index correction). So sánh actual VCB vs synthetic control. | Post-event cumulative impact plot. p-value of impact. | Ch15 NB06 |
| 4.3 | **Factor Zoo Validation** — test tất cả feature group nào có marginal pricing power after controlling for full set. Post-double-selection LASSO. Out-of-sample SPY or VN30 làm pricing outcome. | Factor nào survives double selection? | Ch15 NB11 |
| 4.4 | **Causal Discovery** — PCMCI hoặc NOTEARS trên feature set để khám phá causal graph. Directed edges: feature A → feature B → VCB return? | Directed graph. Cạnh nào robust với subsampling? | Ch15 NB08 |
| 4.5 | **DoWhy Refutation** — với mỗi causal estimate ở 4.1–4.2, chạy refutation: placebo treatment, random common cause, data subset, bootstrap. | Refutation pass/fail table. Claim nào robust? | Ch15 NB10 |

**Yêu cầu:** (a) Refutation battery bắt buộc — mỗi causal claim phải qua ít nhất 3 refutation tests. (b) Không claim causal nếu chưa qua sensitivity analysis.

---

## Phase 5: Strategy + Backtest
> **Mục đích:** Xây dựng và kiểm tra trading strategy dựa trên signals từ Phase 3 + Phase 4

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 5.1 | **Trading protocol** — định nghĩa timing, rebalancing, sizing, fills. VD: daily close signal → next-day open fill; rebalance weekly; size = signal strength × risk budget. | Protocol specification (text). | Ch16 NB01 |
| 5.2 | **Signal → Position mapping** — top 20% predicted return → long (VCB only hoặc thêm bank basket), bottom 20% → short/cash. Hoặc vanilla: forecast → weight = clipped z-score. | Signal → weight function doc. | Ch16 NB04 |
| 5.3 | **Backtest event-driven** — dùng backtest engine. Walk-forward: train/parameter update hàng năm, predict + trade daily. | Equity curve, daily returns, turnover, gross PnL. | Ch16 NB04–NB05 |
| 5.4 | **Cost waterfall** — áp transaction costs lên từng trade. Spread: ước tính 0.05–0.15% (VCB). Market impact: model square-root theo daily volume fraction. | Gross vs net comparison. Breakeven turnover. | Ch18 NB10–NB11 |
| 5.5 | **Portfolio allocation** — thử 3 methods so sánh: (1) equal weight per signal unit, (2) inverse vol target, (3) HRP với bank universe. | Sharpe, drawdown, turnover mỗi method. | Ch17 NB05–NB06 |
| 5.6 | **Conformal position sizing** — dùng CP interval width để scale size. Interval hẹp → larger position. | PnL so sánh vs fixed size. | Ch17 NB07 |
| 5.7 | **Deflated Sharpe Ratio** — hiệu chỉnh SR cho N trials (multiple features, windows, model configs). K = estimated trials count. | DSR ≤ 0 → chiến lược không có edge thực sự. | Ch16 NB11–NB12 |
| 5.8 | **Backtest diagnostics** — regime slices: vol regime (low/med/high), rate cycle (cutting/hiking/stable), VN trend (bull/bear/sideways). | Sharpe theo regime. Strategy nào làm tốt/gục ở regime nào? | Ch16 NB10 |

**Yêu cầu:** (a) DSR là gate cuối. Nếu DSR không reject 0 → stop here. (b) Regime diagnostics fixed = biết strategy hoạt động trong môi trường nào.

---

## Phase 6: Risk & Stress Testing
> **Mục đích:** Kiểm tra strategy sống sót qua các kịch bản khắc nghiệt

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 6.1 | **VaR/CVaR** — daily PnL historical VaR 95%/99%. CVaR vượt VaR bao nhiêu? | VaR table. Nếu CVaR > 2× VaR → tail risk cao. | Ch19 NB01 |
| 6.2 | **Drawdown analysis** — max drawdown, drawdown duration (ngày phục hồi). So sánh vs buy & hold VCB. | Drawdown summary table. | Ch19 NB01 |
| 6.3 | **Stress scenarios** — replay COVID crash (Q1 2020), 2022 VN rate hike, 2023 NPL stress. Strategy PnL trong từng window. | Scenario impact table. Strategy gục ở scenario nào? | Ch19 NB06 |
| 6.4 | **Factor exposure decomposition** — TradeSHAP: explain each trade's PnL theo factor exposures. Có unintended exposure không? | Factor attribution plot. Nếu factor exposure ≠ forecast → alignment issue. | Ch19 NB05 |

**Yêu cầu:** (a) Strategy không deployable nếu max drawdown > 30% hoặc recovery > 12 months. (b) Factor exposure phải aligned với forecast intent.

---

## Phase 7: Final Verification + Synthesis
> **Mục đích:** Pipeline evidence snapshot tổng hợp — quyết định deploy hay không

| Bước | Nội dung | Yêu cầu đầu ra | Tham chiếu |
|------|----------|---------------|------------|
| 7.1 | **Pipeline summary** — feature survival list → model selection → strategy Sharpe → cost gate → DSR → stress test pass | 1-page evidence snapshot (Table 20.11 style) | Ch20 NB08 |
| 7.2 | **Regime risk assessment** — 3 decay mechanisms check: prediction quality drift, portfolio translation drift, structural break. | Risk rating per mechanism. | Ch20 NB07 |
| 7.3 | **Constraints inventory** — data frequency, rebalance cadence, capacity, liquidity, broker access. | Danh sách constraints + giải pháp. | Ch20 NB08 |
| 7.4 | **Next-step ledger** — nếu approve: next steps cho live rollout. Nếu reject: what needs improvement. | Decision + action items. | Ch20 NB08 |
| 7.5 | **Production checklist** — pipeline parity verification, drift monitoring setup, safe rollout steps, kill switch criteria | Checklist completed per Ch25 + Ch26 | Ch25, Ch26 |

**Yêu cầu:** Bước 7 là gate cuối — decide go/no-go dựa trên evidence, không dựa trên narrative.

---

## Phase 8 (If Go): Live Shadow + Rollout
> **Mục đích:** Đưa strategy vào shadow mode, sau đó staged rollout

| Bước | Nội dung | Yêu cầu | Tham chiếu |
|------|----------|---------|------------|
| 8.1 | **Pipeline parity** — verify cùng strategy code cho backtest và live (code identical). | 9/9 parity tests pass | Ch25 NB01, NB08 |
| 8.2 | **Shadow trading** — chạy strategy song song không có tiền thật. Track divergence. | Shadow log: signals match? | Ch25 NB10 |
| 8.3 | **Safe rollout** — shadow → capital-capped → staged allocation. | Rollout plan with gating criteria + rollback | Ch26 NB03 |
| 8.4 | **Drift monitoring setup** — rolling IC, PSI, KS, ADWIN. | Dashboard (Ch26 NB01–02 style) | Ch26 NB01–02 |
| 8.5 | **Circuit breakers** — daily loss, drawdown, consecutive loss, stale data. | 4 breakers with CLOSED/OPEN/HALF_OPEN | Ch26 NB04 |

---

## TỔNG QUAN THỜI GIAN & GATE

```
Phase 1 (Data)          1 tuần   → Gate: feature matrix ready, 40+ features
Phase 2 (Feature Valid) 1 tuần   → Gate: shortlisted features, baseline IC, OLS ready  
Phase 3 (Modeling)      1.5 tuần → Gate: best model + SHAP + CP intervals
Phase 4 (Causal)        1 tuần   → Gate: causal graph + refutation result
Phase 5 (Strategy)      1.5 tuần → Gate: DSR > 0? → tiếp / dừng
Phase 6 (Risk)          0.5 tuần → Gate: stress test pass? → tiếp / dừng
Phase 7 (Synthesis)     0.5 tuần → Gate: go/no-go decision
Phase 8 (Rollout)       ~∞       → Gate: shadow pass → cap-capped → full
```

Mỗi **Gate** là checkpoint: nếu fail gate, dừng lại và phân tích nguyên nhân trước khi tiếp — đây là tinh thần của **process-is-edge** (Ch27).
