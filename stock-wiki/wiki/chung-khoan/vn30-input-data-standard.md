# Chuẩn dữ liệu đầu vào cho phân tích nhóm VN30

> File này kế thừa toàn bộ kiến thức từ [[machine-learning-for-trading]] đã ingest vào wiki.
> Mỗi bước đều có link tới concept page tương ứng trong llm-wiki.

---

## Mục tiêu

Xây dựng chuẩn dữ liệu chung cho **VN30** dựa trên nguyên tắc [[process-is-edge]] — edge bền vững nằm ở quy trình, không nằm ở một model cụ thể.

Phục vụ:
1. Phân tích từng mã (VCB, FPT, HPG...) — [[ch07-defining-the-learning-task]]
2. So sánh tương quan cross-section trong rổ VN30 — [[ols-inference-to-prediction]], [[regularized-regression-trading]]
3. Xây dựng mô hình dự báo — [[ch11-ml-pipeline]] → [[ch12-gradient-boosting]] → [[ch13-dl-time-series]]
4. Backtest chiến lược chọn cổ phiếu — [[ch16-strategy-simulation]], [[deflated-sharpe-ratio]]
5. Quản trị leakage, dữ liệu trễ, corporate actions — [[ch06-strategy-definition]], [[hyperparameter-tuning-validation-bias]]
6. Cung cấp dữ liệu/phân tích qua **Web + MCP server** để AI agent kết nối và chạy phân tích trực tiếp — [[financial-autonomous-agents]], [[react-tool-contracts-memory]], [[ml4t-research-operator]], [[mlops-governance-trading]]

---

## I. Nguyên tắc thiết kế

Dựa trên **[[financial-data-universe]]** (Chương 2 — The Financial Data Universe):

1. **Common-first**: mọi mã VN30 phải có cùng bộ dữ liệu lõi — OHLCV, basic fundamentals, macro. Đây là nguyên tắc từ [[ch08-financial-features]]: không xử lý feature riêng từng mã khi chưa chuẩn hóa.
2. **Point-in-time**: BCTC chỉ dùng từ ngày công bố — tránh [[hyperparameter-tuning-validation-bias]] (look-ahead bias).
3. **Raw immutable**: không sửa dữ liệu gốc — theo đúng mô hình của [[financial-data-universe]].
4. **Sector plugin**: dữ liệu ngành là module riêng — banking ([[ch14-latent-factors]], [[factor-regimes]]), steel ([[ch08-financial-features]]).
5. **Model-ready uniform schema**: cùng format cuối — tuân theo quy tắc từ [[ch11-ml-pipeline]].

---

## II. Các lớp dữ liệu

Pipeline 5 tầng theo [[vn30-data-pipeline-architecture]]:

```
raw/ → standardized/ → features/ → model_ready/
```

---

## III. Danh mục dữ liệu bắt buộc

### 1. Universe table — `vn30_universe.parquet`

- Lưu **lịch sử membership VN30** để tránh survivorship bias — nguyên tắc từ [[financial-data-universe]].
- Cần sector classification để sau này apply [[factor-regimes]] và [[ch14-latent-factors]].

### 2. OHLCV daily — `prices_daily.parquet`

- OHLCV daily cho 30 mã: open, high, low, close, volume, value.
- **adjusted_close + adj_factor** để total return tính đúng — áp dụng [[ch08-financial-features]].
- Một trong những feature quan trọng nhất là **returns và volatility** — tham khảo [[ch08-financial-features]] và [[ch13-dl-time-series]].

### 3. Index / benchmark daily — `index_daily.parquet`

- VNINDEX, VN30, VNMID, VNSMALL — benchmark cho excess return.
- Dùng để tính **beta** ([[ch08-financial-features]]) và xác định **market regime** ([[factor-regimes]], [[regime-backtest-diagnostics]]).

### 4. Fundamentals quarterly — `fundamentals_quarterly.parquet`

**Đây là nguồn quan trọng nhất về mặt data quality.**

Columns bắt buộc: revenue, net_income, eps, bvps, roe, roa, gross_margin, debt_to_equity, current_ratio.

**`publish_date` là mandatory** — dùng để tránh look-ahead bias. Forward-fill chỉ từ publish_date, không từ period_end_date. Đây là triển khai cụ thể của nguyên tắc từ [[ch06-strategy-definition]] về point-in-time data.

Các tỷ lệ tài chính này nuôi [[ch08-financial-features]] và [[ch09-model-based-features]].

### 5. Valuation daily/monthly — `valuation.parquet`

- P/E TTM, P/B, market_cap, dividend_yield.
- Dùng cho **value factor** — một trong những factor quan trọng từ [[factor-regimes]] và [[ch14-latent-factors]].
- Market_cap dùng để rank stocks trong VN30 — [[ols-inference-to-prediction]].

### 6. Corporate actions — `corporate_actions.parquet`

- cash_dividend, stock_dividend, split, rights_issue.
- Nếu không xử lý, total return tính sai → [[strategy-simulation-backtesting]] sẽ sai.

### 7. Macro data — `macro_long.parquet`

Long format (date, indicator, value) cho phép thêm indicator mới dễ dàng.

**Macro tối thiểu:**
- CPI YoY, GDP YoY — từ GSO
- Lãi suất điều hành NHNN, lãi suất liên ngân hàng — từ SBV
- USD/VND — từ SBV/Vietcombank
- Giá dầu Brent, giá vàng — thị trường hàng hóa
- PMI — S&P Global
- Fed Funds Rate — ảnh hưởng dòng vốn ngoại

Macro features được xử lý theo pattern từ [[ch25-live-trading]]: forward-fill macro với ngày công bố, không dùng future data.

### 8. Trading flow / liquidity — `trading_flow.parquet`

- foreign_buy/sell_value, foreign_net_value
- proprietary_net_value, put_through_value
- margin_balance, foreign_room_remaining

Đây là **market microstructure proxy** — phục vụ [[ch08-financial-features]] và [[factor-regimes]].

---

## IV. Dữ liệu đặc thù ngành (sector plugins)

File `sector_specific.parquet` dạng long format: (date, symbol, sector, metric, value, unit, publish_date, source).

### Banking
- NIM, NPL ratio, CAR, CASA, loan/deposit growth, LLR/NPL — các feature fundamental đặc thù ngân hàng.
- Những feature này kết hợp với [[ch14-latent-factors]] (PCA trên cross-section banks) và [[ch09-model-based-features]] (autoencoder representations).
- [[factor-regimes]] cho sector banking riêng: NIM cycle vs credit cycle.

### Real estate
- Inventory/assets, D/E, presales, project handover.
- Kết hợp [[ch08-financial-features]] cho nhóm BĐS.

### Steel
- HRC price, iron ore, coking coal price, export volume.
- Nhóm dữ liệu này khác với banking — cần xử lý riêng nhưng schema chung [[vn30-data-pipeline-architecture]].

### Retail
- Store count, revenue/store, gross margin, inventory turnover, same-store sales growth.
- Feature engineering theo [[ch08-financial-features]].

### Securities
- Market trading value, margin loan, brokerage market share.
- Nhạy với thị trường chung — cần kết hợp [[factor-regimes]] (bull/bear regime).

### Oil & Gas
- Brent, gas price, crack spread.
- Dữ liệu giá hàng hóa ảnh hưởng mạnh — xử lý theo macro pattern [[ch25-live-trading]].

---

## V. Feature engineering từng nhóm

### Price-volume features ([[ch08-financial-features]])
- **returns**: ret_1d, ret_5d, ret_21d, ret_63d, ret_252d
- **volatility**: vol_21d (Parkinson/Garman-Klass), vol_63d
- **technical**: RSI(14), MACD(mid/signal/hist), BB(20,2)
- **volume_zscore**: volume z-score 21d
- **beta_252d**: rolling beta vs VNINDEX
- **relative_strength**: stock_return - VN30_return

### Fundamental features ([[ch08-financial-features]], [[ch09-model-based-features]])
- **Valuation**: pe_ttm, pb, ps, ev_ebitda, dividend_yield
- **Profitability**: roe, roa, gross_margin, net_margin
- **Growth**: revenue_growth_qoq, eps_growth_yoy, roe_change
- **Health**: debt_to_equity, current_ratio, interest_coverage
- **Quality**: accruals (operating_cf / net_income)

### Macro features ([[ch25-live-trading]])
- cpi_yoy, policy_rate, usd_vnd_return, brent_return, pmi
- **Derived**: rate_cycle (cutting/hiking/stable), vol_regime (low/med/high)
- Forward-fill từ publish_date — protocol từ [[ch06-strategy-definition]]

### Sector features
- Tùy ngành: nim, npl (bank); hrc_return (steel); store_count_growth (retail)
- Dùng long format để pipeline generic — đúng [[data-pipeline-standard]]

### Target columns — [[ch07-defining-the-learning-task]]
| Target | Công thức | Horizon |
|--------|-----------|---------|
| fwd_ret_5d | close[t+5] / close[t] - 1 | Ngắn |
| fwd_ret_21d | close[t+21] / close[t] - 1 | 1 tháng |
| fwd_ret_63d | close[t+63] / close[t] - 1 | 1 quý |
| fwd_excess_21d | stock_fwd_ret_21d - VNINDEX_fwd_ret_21d | Stock selection |
| rank_fwd_ret_21d | Rank cross-section trong VN30 | Cross-section model |

---

## VI. Validation protocol — [[ch06-strategy-definition]], [[ch11-ml-pipeline]]

### Walk-Forward Cross-Validation
- Train: 2010–2016, test: 2017, expand yearly.
- **Purged CV** + embargo — tránh [[hyperparameter-tuning-validation-bias]].

### IC Test — [[ch20-strategy-synthesis]], [[signal-quality-feature-triage]]
- Spearman rank correlation: feature[t] vs fwd_ret_21d[t]
- Tính hàng năm: mean IC, ICIR, positive-fold share
- IC decay plot — feature survival ≠ strategy survival

### FDR Control — [[ch06-strategy-definition]], [[signal-quality-feature-triage]]
- Multiple-testing correction (Benjamini-Hochberg)
- Threshold q=0.05
- Harvey (2016) threshold: |t| > 3.0

### DSR — [[deflated-sharpe-ratio]]
- Hiệu chỉnh N trials (features × windows × models)
- Nếu DSR ≤ 0 → không có edge thực sự

### Quality gates trước modeling
1. 8–10 năm daily OHLCV cho phần lớn mã
2. Missing OHLCV < 2%
3. Fundamentals có publish_date
4. Corporate actions có adj_factor
5. Macro không forward-filled trước publish_date
6. No duplicate (date, symbol)
7. Target columns chỉ NaN ở cuối horizon
8. Có benchmark VNINDEX/VN30

---

## VII. Ưu tiên triển khai

### Giai đoạn A — Core VN30 (common)
| Bước | File | Wiki ref |
|------|------|----------|
| 1 | `vn30_universe.parquet` | [[financial-data-universe]] |
| 2 | `prices_daily.parquet` | [[ch08-financial-features]] |
| 3 | `index_daily.parquet` | [[financial-data-universe]] |
| 4 | `fundamentals_quarterly.parquet` | [[ch08-financial-features]] |
| 5 | `valuation.parquet` | [[ch08-financial-features]] |
| 6 | `corporate_actions.parquet` | [[ch16-strategy-simulation]] |
| 7 | `macro_long.parquet` | [[ch25-live-trading]] |
| 8 | `vn30_model_matrix.parquet` | [[ch11-ml-pipeline]] |

### Giai đoạn B — Sector plugins
| Ngành | Feature chính | Wiki ref |
|-------|--------------|----------|
| Banking | NIM, NPL, CAR, CASA | [[ch14-latent-factors]], [[factor-regimes]] |
| BĐS | Inventory, D/E, presales | [[ch08-financial-features]] |
| Thép | HRC, iron ore | [[ch08-financial-features]] |
| Bán lẻ | Store count, GMROI | [[ch08-financial-features]] |
| Chứng khoán | Margin, thị phần | [[ch08-financial-features]] |
| Dầu khí | Brent, gas | [[ch25-live-trading]] |

### Giai đoạn C — Alternative data
| Data | Mục đích | Wiki ref |
|------|---------|----------|
| Foreign flow | Dòng tiền ngoại | → [[ch22-rag-financial-research]] |
| News sentiment | Event detection | → [[ch10-text-feature-engineering]] |
| Analyst RAG | Consensus estimates | → [[rag-financial-research]] |
| Knowledge graph | Entity relationships | → [[financial-knowledge-graphs]] |

---

## VIII. Output cuối pipeline

File `vn30_model_matrix.parquet` — mỗi dòng là `(date, symbol)`:

Bảng này được dùng cho toàn bộ các phân tích sau:
- **Single-stock model** ([[ch07-defining-the-learning-task]], [[ch12-gradient-boosting]]): XGBoost dự báo forward return từng mã
- **Cross-section model** ([[ols-inference-to-prediction]], [[regularized-regression-trading]]): rank stocks trong VN30
- **Factor decomposition** ([[ch14-latent-factors]], [[factor-zoo-validation]]): PCA/IPCA trên panel
- **Causal analysis** ([[causal-ml-trading]], [[double-machine-learning]]): DML cho lãi suất → VCB return
- **Backtest** ([[ch16-strategy-simulation]], [[deflated-sharpe-ratio]]): strategy simulation
- **Portfolio** ([[hierarchical-risk-parity]], [[conformal-position-sizing]], [[portfolio-construction-ml]]): HRP, conformal sizing
- **Risk management** ([[risk-management-ml]], [[var-cvar-path-risk]], [[stress-testing-drift]]): VaR, stress test
- **Transaction cost** ([[transaction-costs-ml]], [[almgren-chriss-execution]], [[cost-taxonomy-asset-class]]): net sau costs
- **Live deployment** ([[unified-backtest-live-framework]], [[pipeline-verification-live]], [[mlops-governance-trading]], [[drift-monitoring-performance]], [[circuit-breakers]]): production readiness
- **MCP Server for AI Agents** ([[financial-autonomous-agents]], [[react-tool-contracts-memory]], [[ml4t-research-operator]]): expose toàn bộ data + model + backtest qua MCP tools để AI (Claude, Cursor, Hermes…) kết nối và phân tích trực tiếp

---

## X. MCP Server — Kết nối AI phân tích

Để AI agent có thể kết nối trực tiếp vào data pipeline và thực hiện phân tích, xây dựng **MCP Server** (Model Context Protocol) wrapper xung quanh toàn bộ hệ thống.

### Kiến trúc

AI Agent <-- MCP Protocol --> MCP Server (Python FastMCP) --> reads/writes --> Data Layer (Parquet)

### Danh sách tool MCP

| Tool | Đầu vào | Đầu ra | Wiki ref |
|---|---|---|---|
| `list_universe` | — | Danh sách mã + ngành | [[financial-data-universe]] |
| `query_prices` | symbol, from, to | OHLCV daily | [[ch08-financial-features]] |
| `query_fundamentals` | symbol, from, to | BCTC quarterly | [[ch08-financial-features]] |
| `query_macro` | indicator, from, to | Macro time series | [[ch25-live-trading]] |
| `compute_features` | symbols, from | Feature matrix | [[ch08-financial-features]], [[ch09-model-based-features]] |
| `ic_analysis` | symbol, features | IC, ICIR, FDR table | [[signal-quality-feature-triage]] |
| `train_predict` | symbols, horizon, model | Predictions + metrics | [[ch12-gradient-boosting]], [[ch11-ml-pipeline]] |
| `run_backtest` | strategy params | Equity curve, Sharpe, DSR | [[ch16-strategy-simulation]], [[deflated-sharpe-ratio]] |
| `portfolio_optimize` | symbols, method | Portfolio weights | [[hierarchical-risk-parity]], [[conformal-position-sizing]] |
| `risk_report` | portfolio | VaR, drawdown, stress | [[risk-management-ml]], [[stress-testing-drift]] |
| `causal_estimate` | treatment, outcome, controls | ATE + refutation | [[causal-ml-trading]], [[double-machine-learning]] |
| `generate_report` | symbols, type | Markdown report | [[strategy-synthesis-pipeline]] |

### Công nghệ

| Thành phần | Công nghệ | Lý do |
|-----------|----------|-------|
| MCP framework | `fastmcp` / Python MCP SDK | Chuẩn MCP chính thức, tương thích Claude Desktop, Cursor |
| Web server | FastAPI + uvicorn | Async, tích hợp MCP và REST |
| Data engine | Polars | Xử lý Parquet nhanh, thay thế Pandas |
| Storage | Parquet (file system) | Đã có sẵn từ data pipeline |
| ML | XGBoost + Optuna + sklearn | Giống ML4T code |
| Portfolio | riskfolio-lib / PyPortfolioOpt | Portfolio optimization |
| Auth | API key / Bearer token | Bảo vệ MCP server |
| Deploy | Docker trên VPS | Tái sử dụng setup Docker hiện tại |

### Lộ trình triển khai MCP

| Giai đoạn | Nội dung | Tuần |
|-----------|----------|------|
| 1 | MCP skeleton: list_universe, query_prices, query_fundamentals | 1 |
| 2 | Feature + Model: compute_features, ic_analysis, train_predict | 2 |
| 3 | Strategy: run_backtest, portfolio_optimize, risk_report | 3 |
| 4 | Causal + Report: causal_estimate, generate_report + Docs | 4 |

---

## XI. Tổng kết: bản đồ wiki sử dụng

```
          [[process-is-edge]] — triết lý nền tảng
                    │
          [[financial-data-universe]] — loại dữ liệu
                    │
     ┌──────────────┼──────────────┐
     ▼              ▼              ▼
[[ch08-financial-features]]   [[ch06-strategy-definition]]   [[ch25-live-trading]]
     │              │              │
     ▼              ▼              ▼
Feature engineering    Validation protocol    Macro processing
     │
     ├──→ [[ch12-gradient-boosting]] + [[ch13-dl-time-series]] → prediction
     ├──→ [[ch14-latent-factors]] + [[causal-ml-trading]] → factor analysis
     ├──→ [[ch16-strategy-simulation]] + [[deflated-sharpe-ratio]] → backtest
     ├──→ [[ch17-portfolio-construction]] + [[hierarchical-risk-parity]] → portfolio
     └──→ [[ch19-risk-management]] + [[transaction-costs-ml]] → risk & cost
     
          [[ch20-strategy-synthesis]] — pipeline synthesis
                    │
          [[ch25-live-trading]] + [[ch26-mlops-governance]] — production
```

---

*Toàn bộ các link [[wiki-concept]] đều trỏ tới trang đã ingest từ stefan-jansen/machine-learning-for-trading và lưu tại `wiki/concepts/`.*
