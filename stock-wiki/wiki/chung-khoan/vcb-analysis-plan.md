# Hệ thống hóa kiến thức ML4T — Ứng dụng phân tích VCB

Dưới đây là toàn bộ kiến thức từ **stefan-jansen/machine-learning-for-trading** (28 chương) đã được hệ thống hóa thành lộ trình phân tích mã VCB.

---

## I. TỔNG QUAN HỆ THỐNG (27 chương đã ingest)

| Pha | Chương | Nội dung | Trạng thái |
|-----|--------|----------|-----------|
| **0. Nền tảng** | 1-2 | Process là edge, dữ liệu tài chính | ✅ |
| **1. Dữ liệu & Feature** | 5-10 | Synthetic data, feature engineering, NLP, model-based features | ✅ |
| **2. Modeling** | 11-15 | ML Pipeline, GBM/XGB/LightGBM, DL time series, latent factors, causal estimation | ✅ |
| **3. Strategy & Portfolio** | 16-19 | Backtest, portfolio construction, transaction costs, risk management | ✅ |
| **4. Synthesis & Production** | 20-27 | Strategy synthesis + RL execution + RAG + KG + agents + live trading + MLOps | ✅ |

---

## II. LỘ TRÌNH 5 GIAI ĐOẠN PHÂN TÍCH VCB

### GIAI ĐOẠN 1: DỮ LIỆU & FEATURE ENGINEERING

**Mục tiêu:** Thu thập và xây dựng feature set cho VCB.

**Dữ liệu cần:**
- **Giá & khối lượng** VCB (HOSE): OHLCV hàng ngày từ 2010 → nay
- **Chỉ số VN-Index / VN30** làm benchmark
- **Báo cáo tài chính** quarterly: EPS, BVPS, ROE, NIM, NPL, CAR
- **Dữ liệu vĩ mô**: lãi suất điều hành NHNN, CPI, tín dụng, tỷ giá USD/VND
- **Alternative data** (nếu có): tin tức ngành ngân hàng, giao dịch NĐTNN

**Feature categories (từ Ch8, Ch9, Ch10, Ch25):**
1. **Price-Volume features** (Ch8):
   - Returns: daily, weekly, monthly (1d, 5d, 21d, 63d)
   - Volatility: rolling 21d, 63d, Parkinson/Garman-Klass vol
   - Technical: RSI(14), MACD, BB, volume-weighted momentum
2. **Fundamental features** (Ch8):
   - P/B, P/E, ROE, NIM, NPL ratio, CAR
   - YoY growth: EPS growth, loan growth, deposit growth
   - Accounting accruals, quality metrics
3. **Macro features** (Ch8, Ch25):
   - Lãi suất NHNN (refinancing, discount, OMO)
   - CPI inflation, credit growth, PMI
   - USD/VND exchange rate, gold price
4. **Model-based features** (Ch9):
   - PCA từ cross-section bank universe
   - Autoencoder representations
5. **Text features** (Ch10, Ch22):
   - Sentiment từ tin tức VCB (FinBERT/BERT-VN)
   - RAG pipeline cho analyst reports
6. **Feature validation** (Ch6, Ch20):
   - **IC test**: mỗi feature với forward return 5d/21d
   - **FDR control**: multiple-testing correction
   - **Survival analysis**: feature nào hiệu quả qua thời gian

**Kiểm tra feature quality (Ch20):**
- IC (Information Coefficient): sign, magnitude, stability
- ICIR (IC Information Ratio)
- Positive-fold share
- FDR-controlled feature triage

**Công cụ:** Python + Polars/Pandas; vẽ correlation matrix, IC decay plot, PSI drift

---

### GIAI ĐOẠN 2: MODELING & CROSS-VALIDATION

**Mục tiêu:** Xây dựng mô hình dự báo forward return VCB với OOS validation nghiêm ngặt.

**Target (label) engineering (Ch7, Ch11):**
- Forward return 5-day, 21-day (1 tháng)
- Forward return 63-day (1 quý)
- Phân loại: top/bottom tercile, hoặc continuous regression

**Model candidates (Ch11, Ch12, Ch13):**
1. **Baseline: OLS Linear** (Ch11) — benchmark, không kỳ vọng outperform
2. **Regularized: Ridge/LASSO** (Ch11) — handle multicollinearity
3. **Ensemble: XGBoost / LightGBM / CatBoost** (Ch12) — primary candidate
   - Hyperparameter tuning: Optuna (Ch12)
   - Feature importance: TreeSHAP (Ch12)
4. **Time Series DL: LSTM / GRU** (Ch13) — nếu đủ data daily
5. **Conformal Prediction** (Ch12) — prediction intervals cho uncertainty

**Validation protocol (Ch6, Ch7, Ch11):**
- **Walk-Forward Cross-Validation** — train/validation expanding window, test rolling
- **Purged CV** — avoid label leakage from adjacent observations
- **Embargo** — gap giữa train và test để tránh serial correlation contamination

**Chống overfitting:**
- **Multiple Testing** (Ch6, Ch7): minimum t-stat threshold (Harvey 2016: |t| > 3.0)
- **Deflated Sharpe Ratio** (Ch16): hiệu chỉnh selection bias
- **Conformal prediction** (Ch11, Ch12): prediction intervals

**Checkpoint (Ch26):**
- Log mỗi experiment vào MLflow (Ch26 NB06) với training_runs, prediction_sets, backtest_runs, cohort_metrics
- So sánh ranking parity giữa các model (Ridge vs XGB vs LSTM)

---

### GIAI ĐOẠN 3: CAUSAL & FACTOR ANALYSIS

**Mục tiêu:** Không chỉ predict, mà hiểu **tại sao** VCB di chuyển.

**Các câu hỏi causal (Ch15):**
1. **Lãi suất NHNN → VCB returns?** — Double Machine Learning (DML) + BSTS
2. **Credit growth → VCB outperformance?** — Causal Forest
3. **NPL ratio surprise → VCB drawdown?** — Event study (BSTS)
4. **GDP forecast revision → banking sector?** — Causal discovery

**Causal toolkit (Ch15):**
- **DML (Double Machine Learning)**: orthogonalization + cross-fitting
- **BSTS (Bayesian Structural Time Series)**: event study cho discrete shocks
- **DoWhy**: refutation battery (placebo, sensitivity, block permutation)
- **Causal Discovery**: PCMCI, NOTEARS, VAR-LiNGAM

**Factor decomposition (Ch14, Ch15):**
- **Factor Zoo** (Ch15 NB11): post-double-selection LASSO — feature nào thực sự có marginal pricing power?
- **IPCA / Autoencoder** (Ch14): latent factors từ bank universe
- **Eigenportfolios** (Ch14): top PCA portfolios

**Factor validation (Ch15):**
- Double-selection: pricing LASSO + correlation LASSO
- Hold-out SPY-level asset: outcome phải ngoài column span của controls
- Refutation battery bắt buộc

---

### GIAI ĐOẠN 4: STRATEGY & PORTFOLIO

**Mục tiêu:** Biến signal thành portfolio weights và backtest.

**Strategy design (Ch6, Ch16):**
- **Trading protocol**: timing (daily/weekly), rebalancing, sizing, fills, costs, constraints
- **Signal → Position**: ví dụ top quintile long, bottom quintile short
- **Stateful strategies**: trailing stop, take profit, order book (Ch16)

**Multiple engine comparison (Ch16):**
- Vectorized vs Event-driven
- Engine parity (NB06, NB07): cùng strategy, khác engine → khác equity curve

**Portfolio allocation (Ch17):**
- **HRP** (Hierarchical Risk Parity) — corporate bond HRP
- **Volatility parity** — dễ hiểu, robust
- **Kelly criterion** — fractional Kelly cho growth
- **Conformal position sizing** (Ch17 NB07) — uncertainty-based sizes
- **DL portfolio** — SoftMin allocation, VLSTM end-to-end

**Transaction costs (Ch18):**
- **Cost taxonomy**: explicit (commission, tax, stamp duty) vs implicit (spread, slippage, market impact)
- **Market impact calibration** (Ch18 NB03): VCB daily volume → impact model
- **Breakeven turnover** (Ch18 NB11)
- **Gross vs net**: cost waterfall (Ch18 NB10)

**Backtest baseline (Ch16):**
- Buy & hold VCB (1/N portfolio)
- Inverse vol
- Naive momentum (time-series)

**Backtest diagnostics (Ch16):**
- Drawdown depth/duration
- Regime conditioning (volatility, trend, rate cycle)
- DSR hiệu chỉnh selection bias

**Risk management (Ch19):**
- VaR/CVaR
- MAE/MFE trade analysis
- Factor exposure decomposition
- Stress testing: COVID, 2022 rate hike
- Kill switch criteria

---

### GIAI ĐOẠN 5: SYNTHESIS, PRODUCTION & GOVERNANCE

**Mục tiêu:** Kết luận và chuẩn bị cho monitoring thực tế.

**Pipeline synthesis (Ch20):**
- Feature survival ≠ strategy survival
- IC → Sharpe gap tồn tại
- Regime risk: 3 decay mechanisms
  - Prediction quality drift
  - Portfolio translation drift
  - Structural break
- Cost survival: breakeven scorecard

**Live deployment readiness (Ch25, Ch26):**
- Unified framework: cùng strategy code cho backtest/paper/live
- Pipeline parity verification
- SafeBroker: kill switch, shadow mode, startup reconciliation
- Order lifecycle FSM

**Governance (Ch26):**
- Drift monitoring: PSI, K-S, ADWIN, DDM
- Safe model rollout: shadow mode → capped A/B → staged
- Circuit breakers: drawdown, daily loss, latency
- Feast feature store + MLflow
- Backtest-to-live realization ratio tracking

---

## III. LỘ TRÌNH THỰC HIỆN (RECOMMENDED)

```
Tuần 1:  🟢 Data Engineering
        ├── Crawl VCB OHLCV từ 2010 (Cafef/SSI)
        ├── Crawl financial statements quarterly
        ├── Macro data: NHNN rates, CPI, credit, USD/VND
        └── Xây feature matrix Polars/Parquet

Tuần 2:  🟢 Feature Validation + Baseline Models
        ├── IC test từng feature vs forward return 5d/21d/63d
        ├── FDR control threshold
        ├── Baseline OLS + Ridge walk-forward
        └── IC decay plot, correlation heatmap

Tuần 3:  🟡 Primary Modeling
        ├── XGBoost/LightGBM walk-forward CV
        ├── Optuna HPO + TreeSHAP analysis
        ├── Conformal prediction intervals
        └── Compare vs baseline: IC, Sharpe, hit rate

Tuần 4:  🟡 Causal + Factor Analysis
        ├── DML: feature nào thực sự có causal impact?
        ├── Factor zoo validation: post-double-selection
        ├── BSTS: event studies (rate decisions)
        └── Factor decomposition

Tuần 5:  🟠 Strategy + Backtest
        ├── Signal → Position mapping (top K long/short)
        ├── Backtest with rolling walk-forward
        ├── Cost waterfall: spread, slippage, impact
        ├── HRP allocation + conformal sizing
        └── Deflated Sharpe Ratio

Tuần 6:  🔴 Validation & Governance
        ├── Stress tests: COVID/schock scenarios
        ├── Pipeline parity verification
        ├── Drift monitoring setup
        ├── Safe model rollout procedure
        └── Báo cáo tổng hợp với pipeline evidence snapshot

Mỗi phase có checkpoint để quyết định tiếp hay stop.
```

---

## IV. NGUYÊN TẮC CỐT LÕI (từ Ch27)

1. **Process > Strategy** — edge bền vững từ quy trình, không từ một model
2. **Falsifiable hypotheses** — mỗi step phải xác định được điều kiện fail
3. **OOS validation là bắt buộc** — không backtest multiple lần trên cùng data
4. **Multiple-testing correction** — DSR / t-stat threshold
5. **Feature survival ≠ strategy survival**
6. **Cost survival là gate** — gross return không deployable nếu net thua
7. **Causal claim cần refutation battery**
8. **Drift monitoring sau deployment** — mọi model decay
