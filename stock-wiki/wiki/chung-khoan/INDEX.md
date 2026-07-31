---
tags: [chung-khoan, index]
created: 2026-07-05
---

# Phân tích chứng khoán

## Các trang

- [[machine-learning-for-trading]] — tổng quan dự án (19.5k ⭐)
- [[bao-cao-phan-tich-chuyen-sau-ml-trading-2026]] — báo cáo chuyên sâu ML4T
- [[process-is-edge]] — Chương 1: The Process Is Your Edge
- [[factor-regimes]] — GMM regime detection (AQR factors, 1927-2024)
- [[factor-regimes-full-notebook]] — toàn bộ notebook gồm markdown + code + output
- [[macro-regimes-full-notebook]] — macro regime detection bằng FRED + S&P 500 validation
- [[financial-data-universe]] — Chương 2: The Financial Data Universe
- [[ch05-synthetic-data]] — Chương 5: Synthetic Financial Data
- [[ch06-strategy-definition]] — Chương 6: Strategy Research Framework
- [[ch07-defining-the-learning-task]] — Chương 7: Defining the Learning Task
- [[ch08-financial-features]] — Chương 8: Financial Feature Engineering
- [[ch09-model-based-features]] — Chương 9: Model-Based Feature Extraction
- [[ch10-text-feature-engineering]] — Chương 10: Text Feature Engineering
- [[ch11-ml-pipeline]] — Chương 11: The Machine Learning Pipeline
- [[ch12-gradient-boosting]] — Chương 12: Gradient Boosting and Advanced Tabular Models
- [[ch13-dl-time-series]] — Chương 13: Deep Learning for Time Series
- [[ch14-latent-factors]] — Chương 14: Latent Factor Models
- [[ch15-causal-estimation]] — Chương 15: Causal Estimation
- [[ch16-strategy-simulation]] — Chương 16: Strategy Simulation
- [[ch17-portfolio-construction]] — Chương 17: Portfolio Construction
- [[ch18-transaction-costs]] — Chương 18: Transaction Costs
- [[ch19-risk-management]] — Chương 19: Risk Management
- [[ch20-strategy-synthesis]] — Chương 20: Strategy Synthesis
- [[ch21-rl-execution-hedging]] — Chương 21: RL Execution and Hedging
- [[ch22-rag-financial-research]] — Chương 22: RAG for Financial Research
- [[ch23-knowledge-graphs]] — Chương 23: Knowledge Graphs for Financial AI
- [[ch24-autonomous-agents]] — Chương 24: Autonomous Agents
- [[ch25-live-trading]] — Chương 25: Live Trading Systems
- [[ch26-mlops-governance]] — Chương 26: MLOps and Governance
- [[ch27-systematic-edge]] — Chương 27: The Systematic Edge
- [[two-sigma-regime-modeling]] — Two Sigma GMM regime modeling (4 regimes, 17 factors)
- [[gemini-share]] — ghi chú từ Gemini (cần export thủ công)
- [[vcb-analysis-plan]] — kế hoạch phân tích VCB theo ML4T
- [[vcb-analysis-plan-detailed]] — 8 phase phân tích VCB chi tiết
- [[data-pipeline-standard]] — chuẩn pipeline dữ liệu chứng khoán chung
- [[vn30-input-data-standard]] — chuẩn dữ liệu đầu vào cho phân tích VN30

## Tài liệu thiết kế hiện tại

- [[vn30-input-data-standard]] — ưu tiên hiện tại: chuẩn dữ liệu đầu vào VN30
- [[vn30-data-pipeline-architecture]] — sơ đồ kiến trúc pipeline 5 tầng
- [[data-pipeline-standard]] — chuẩn hóa thư mục raw/standardized/features/model_ready
- [[vcb-analysis-plan-detailed]] — blueprint phân tích VCB từ dữ liệu → model → backtest → governance

## Concepts mới (Chương 27 — The Systematic Edge)

- [[systematic-edge]] — process is the durable edge, alpha factory blueprint
- [[quant-career-learning-path]] — 5 archetypes, T-shaped expertise, learning discipline
- [[quant-frontiers-ethics]] — quantum, DeFi, ethical/auditable AI


## Concepts mới (Chương 26 — MLOps and Governance)
- [[mlops-governance-trading]] — detection/response/automated safety governance model
- [[drift-monitoring-performance]] — PSI, K-S, rolling IC/hit-rate, ADWIN/DDM
- [[safe-model-rollout]] — shadow mode, capped A/B, staged allocation, rollback
- [[circuit-breakers]] — drawdown/loss/latency breakers with CLOSED/OPEN/HALF_OPEN
- [[feast-mlflow-infrastructure]] — feature store, point-in-time joins, MLflow registry

## Concepts mới (Chương 25 — Live Trading)

- [[live-trading-systems]] — live trading frameworks, SafeBroker, staged rollout
- [[unified-backtest-live-framework]] — dual-mode architecture, ETF deployment loop
- [[broker-integration-live-trading]] — IBKR, Alpaca, QuantConnect integration
- [[order-lifecycle-state-machine]] — FSM with 10 states, 19 transitions, crash recovery
- [[pipeline-verification-live]] — parity tests across data/features/predictions/orders
- [[runtime-safety-risk-controls]] — SafeBroker, kill switch, stale data, shadow mode

## Concepts mới (Chương 24 — Autonomous Agents)

- [[financial-autonomous-agents]] — agentic workflows for read-only financial forecasting
- [[react-tool-contracts-memory]] — ReAct reasoning, typed tools, state checkpointing, replay
- [[research-agent-workflow]] — evidence-first single agent with quality gates, calibrated forecasts
- [[multi-agent-forecasting]] — aggregation, debate, supervisor, probability calibration
- [[agent-evaluation-governance]] — scoring, replay, observability, security, contamination controls
- [[ml4t-research-operator]] — thin orchestrator; skill-based experiment executor

## Concepts mới (Chương 23 — Knowledge Graphs)

- [[financial-knowledge-graphs]] — entities→nodes, relationships→edges, provenance→properties
- [[kg-construction-finance]] — LLM extraction; identity, schema, provenance contracts; Neo4j
- [[graph-rag-finance]] — deterministic relational retrieval vs vector RAG
- [[kg-features-and-network-portfolios]] — graph features, GNN embeddings, network portfolios
- [[temporal-kg-leakage]] — 3-timestamp model: event/disclosure/extraction

## Concepts mới (Chương 22 — RAG for Financial Research)

- [[rag-financial-research]] — evidence-grounded LLMs for finance
- [[rag-ingestion-embeddings-retrieval]] — SEC ingestion, domain embeddings, hybrid retrieval, RAGAs
- [[rag-applications-finance]] — 10-K assistant, ESG RAG vs fine-tune, 13F graph, security

## Concepts mới (Chương 21 — RL Execution and Hedging)

- [[rl-execution-hedging]] — RL as sequential control: execution, market making, hedging
- [[rl-algorithms-environments]] — DQN/PPO/A2C, MDP environment/calibration utilities
- [[deep-hedging-irl-sim2real]] — pfhedge, inverse RL, sim-to-real gap

## Concepts mới (Chương 20 — Strategy Synthesis)

- [[strategy-synthesis-pipeline]] — 9 case studies through standardized pipeline
- [[signal-quality-feature-triage]] — FDR triage, IC/ICIR/positive-fold bundle
- [[signal-to-cost-survival]] — Fundamental Law, allocator, breakeven scorecard
- [[regime-risk-strategy-recommendations]] — 3 decay mechanisms, per-CS next steps

## Concepts mới (Chương 19 — Risk Management)

- [[risk-management-ml]] — risk as system design, not post hoc reporting
- [[var-cvar-path-risk]] — VaR/CVaR, drawdown depth/duration, MAE/MFE, exit strategies
- [[factor-exposure-trade-shap]] — factor decomposition, TradeSHAP diagnostics
- [[stress-testing-drift]] — crisis replay, hypothetical scenarios, drift monitoring
- [[ml-exit-deep-hedging]] — two-model entry/exit, deep hedging (Buehler 2019)

## Concepts mới (Chương 18 — Transaction Costs)

- [[transaction-costs-ml]] — costs as workflow constraint, not backtest adjustment
- [[cost-taxonomy-asset-class]] — explicit/implicit/capacity, spread estimation, market impact
- [[almgren-chriss-execution]] — TWAP/VWAP, volume participation, ML dynamic, AC framework
- [[gross-vs-net-performance]] — gross vs net gap, cost cliff, frequency tradeoff
- [[transaction-cost-analysis]] — TCA recalibration, breakeven turnover, kill criteria

## Concepts mới (Chương 17 — Portfolio Construction)

- [[portfolio-construction-ml]] — allocation = expected returns + covariance + constraints
- [[portfolio-evaluation-metrics]] — Sharpe, IR, active share, HHI, leverage stability
- [[mvo-robust-kelly]] — MVO Markowitz Curse, robust optimization, fractional Kelly
- [[hierarchical-risk-parity]] — HRP: clustering + quasi-diagonalization + recursive bisection
- [[conformal-position-sizing]] — uncertainty-based sizing; +5.5% ETFs, -24.8% futures
- [[dl-portfolio-allocation]] — end-to-end DL portfolio: DL, VLSTM, DeePM (SoftMin)
- [[allocator-comparison-protocol]] — controlled comparison, NB09 capstone, factor evidence

## Concepts mới (Chương 16 — Strategy Simulation)

- [[strategy-simulation-backtesting]] — backtest as falsification, not proof
- [[backtest-trading-protocol]] — timing, rebalancing, sizing, fills, costs, constraints
- [[vectorized-vs-event-driven]] — array-based vs sequential simulation semantics
- [[performance-reporting-framework]] — gross/net returns, drawdown, turnover, regime-sliced
- [[regime-backtest-diagnostics]] — aggregate stats can mislead; slice by volatility/trend
- [[deflated-sharpe-ratio]] — DSR, RAS protocol, Reality Check — search-aware inference
- [[engine-parity-backtest]] — same strategy, different engines → different equity curves
- [[stateful-cost-sensitive-backtest]] — trailing stops, order book state, cost sensitivity
- [[ml-backtest-baseline]] — baseline ETF strategy, prediction ≠ trading quality

## Concepts mới (Chương 15 — Causal Estimation)

- [[causal-ml-trading]] — DML, BSTS, causal discovery: từ predictive sang causal
- [[double-machine-learning]] — orthogonalization + cross-fitting để ước lượng causal effect
- [[bsts-event-study]] — Bayesian structural time-series cho discrete events
- [[causal-discovery-methods]] — PCMCI, NOTEARS, VAR-LiNGAM, Granger; hypothesis generators
- [[causal-validation-refutation]] — DoWhy workflow, placebo, sensitivity, block-permutation
- [[factor-zoo-validation]] — double-selection LASSO: factors nào thật sự được priced?
- [[causal-case-study-insights]] — HAC significance vs refutation survival, confounding pervasive

## Concepts mới (Chương 14 — Latent Factor Models)

- [[latent-factor-models]] — attribution vs priced factors; PCA/IPCA/RP-PCA/CAE/SDF
- [[pca-latent-factors]] — PCA for returns, sector ETFs, yield curve level/slope/curvature
- [[eigenportfolios]] — PCA eigenvectors as portfolio weights, HPCA, stat-arb
- [[ipca-rpca]] — characteristic-driven betas và pricing-error objective
- [[conditional-autoencoder-asset-pricing]] — Gu-Kelly-Xiu CAE, nonlinear latent factors
- [[stochastic-discount-factor-dl]] — adversarial SDF + supervised autoencoder
- [[latent-factor-case-studies]] — Marchenko-Pastur breadth diagnostic across case studies

## Concepts mới (Chương 13 — Deep Learning for Time Series)

- [[dl-time-series-forecasting]] — LSTM/GRU → N-BEATS → Transformers → TCN/TSMixer/Mamba → foundation models
- [[recurrent-architectures-lstm]] — LSTM/GRU baseline, vanishing gradients, sequential bottleneck
- [[nbeats-forecasting]] — interpretable trend/seasonality decomposition
- [[ts-great-debate]] — simple linear baselines vs time-series Transformers
- [[time-series-transformers]] — PatchTST, iTransformer, TFT architecture selection
- [[alternative-ts-architectures]] — TCN, TSMixer, Mamba SSM, CNN GAF/MTF encoding
- [[time-series-foundation-models]] — Chronos/TTM/Moirai, zero-shot transfer gap
- [[dl-uncertainty-estimation]] — MC Dropout, Deep Ensembles for position sizing
- [[ts-library-landscape]] — sktime unified forecasting interface
- [[dl-case-study-insights]] — DL vs Ridge/GBM/TabM across case studies

## Concepts mới (Chương 12 — Gradient Boosting)

- [[gradient-boosting-trading]] — GBMs cho tabular financial prediction
- [[ensemble-foundations-finance]] — Random Forest vs Gradient Boosting: bagging vs boosting
- [[gbm-library-benchmark]] — XGBoost/LightGBM/CatBoost comparison, learning-to-rank, monotonic constraints
- [[dl-vs-gbm-tabular]] — TabPFN/TabM/TabR vs GBMs cho tabular finance
- [[optuna-hyperparameter-tuning]] — TPE, pruning, walk-forward HPO, fANOVA
- [[multi-objective-hpo]] — Pareto front: IC vs turnover, cross-asset transfer
- [[treeshap-interpretability]] — TreeSHAP, interactions, drift monitoring, NLP attribution
- [[xai-limitations-rashomon]] — explanation instability, Rashomon effect
- [[conformal-prediction-gbm]] — conformal intervals cho GBM regression
- [[gbm-case-study-insights]] — GBMs across 9 asset classes, holdout decay, model/label/horizon fit

## Concepts mới (Chương 11 — ML Pipeline)

- [[ml-pipeline-trading]] — OLS → regularized regression → SHAP → conformal → backtest
- [[ols-inference-to-prediction]] — từ unbiased estimation sang stable OOS forecasts
- [[regularized-regression-trading]] — Ridge/LASSO/Elastic Net, walk-forward, leakage-safe
- [[logistic-classification-trading]] — direction prediction, calibration, class imbalance
- [[hyperparameter-tuning-validation-bias]] — nested CV vs single-loop, selection bias
- [[shap-model-interpretability]] — SHAP values, feature attribution stability, debugging
- [[conformal-prediction-trading]] — split-conformal, ACI, CQR, coverage monitoring
- [[ml-backtest-baseline]] — IC ≠ portfolio alpha; turnover, costs, momentum baseline

## Concepts mới (Chương 10 — Text Feature Engineering)

- [[text-feature-engineering]] — pipeline biến financial text thành trading features point-in-time safe
- [[financial-nlp-representations]] — lexical/TF-IDF → static embeddings → contextual Transformers
- [[word2vec-asset-embeddings]] — Word2Vec trên 13F portfolios; stocks as words, portfolios as sentences
- [[transformers-for-financial-text]] — self-attention, FinBERT/ModernBERT, fine-tuning workflow
- [[finbert-distribution-shift]] — same-label ≠ same-distribution; PhraseBank vs FinMarBa
- [[financial-ner-extraction]] — NER cho ORG, MONEY, DATE, PER, PERCENT trong financial text
- [[news-text-alpha-signals]] — FNSPID news surprise, sentiment momentum, coverage signals
- [[text-feature-signal-evaluation]] — IC/ICIR/quintile spread evaluation cho text features
- [[sec-filing-text-signals]] — SEC 10-Q MD&A sentiment + narrative change factors

## Concepts mới (Chương 9 — Model-Based Features)

- [[model-based-feature-extraction]] — khái niệm tổng quan: model-based vs direct features
- [[stationarity-diagnostic-features]] — ADF/KPSS decision matrix, rolling stationarity regime, ARCH effects
- [[structural-break-features]] — Zivot-Andrews, Bai-Perron, CUSUM, MOSUM, ADIA Lab break classification
- [[fractional-differencing]] — FFD: d∈(0,1), asset class d recommendations, memory-stationarity tradeoff
- [[kalman-filter-features]] — level/trend/innovation/uncertainty, dynamic hedge ratio, pairs trading
- [[spectral-wavelet-features]] — wavelet decomposition (research), rolling FFT (production), Welch's PSD
- [[path-signature-features]] — iterated integrals, depth truncation, log-signature, lead-lag detection
- [[volatility-model-features]] — ARIMA residuals, GARCH/EGARCH conditional vol, HAR model, Hurst exponent, rough volatility
- [[uncertainty-as-feature]] — Bayesian posterior widths, conformal prediction, forecast uncertainty
- [[regime-features]] — HMM, Markov-switching AR, Wasserstein clustering, regime-as-feature vs mixture of experts
- [[panel-temporal-features]] — cross-sectional ranking, cointegration, O-U half-life, multi-asset aggregation

## Concepts mới (Chương 8 — Financial Features)

- [[feature-design-grammar]] — 3-step filter: horizon alignment, driver hypothesis, role separation
- [[price-volume-features]] — trend, reversal, volatility, volume, cross-sectional normalized từ OHLCV
- [[microstructure-features]] — Kyle Lambda, Amihud, OFI, liquidity, flow vs state
- [[structural-cross-instrument-features]] — carry, term structure, relative value, options-implied
- [[slow-moving-contextual-features]] — fundamentals, macro, calendar; point-in-time ASOF join
- [[feature-selection-dedup]] — correlation filter, clustering, BH-FDR, stability selection
- [[robustness-sensitivity-analysis]] — parameter sweep, near-optimal region, regime-conditional IC
- [[event-studies]] — AAR/CAAR, market model, event window, confidence bands

## Concepts mới (Chương 7 — Defining the Learning Task)

- [[learning-task-definition]] — xác định bài toán học trước modeling
- [[data-quality-diagnostics]] — kiểm tra chất lượng dữ liệu trước preprocessing
- [[train-only-preprocessing]] — fit preprocessing chỉ trên train để tránh leakage
- [[label-engineering]] — thiết kế target/label cho financial ML
- [[mfe-mae-analysis]] — đo đường đi thuận lợi/bất lợi của trade
- [[information-coefficient]] — đánh giá khả năng rank của signal
- [[ic-inference]] — HAC/block bootstrap cho IC
- [[multiple-testing-selection-bias]] — kiểm soát false discovery khi thử nhiều ý tưởng
- [[causal-sanity-checks]] — kiểm tra cơ chế hợp lý của signal

## Concepts mới (Chương 6 — Strategy Definition)

- [[strategy-research-framework]] — trading strategy là executable decision process
- [[research-loop-vs-live-loop]] — phân tách research loop và live trading loop
- [[strategy-map-edge]] — strategy families × sources of edge
- [[trading-setup-definition]] — versioned trading setup, constraints, costs
- [[model-signal-strategy-metrics]] — tách model diagnostics, signal diagnostics, strategy outcomes
- [[walk-forward-evaluation]] — walk-forward, purging, embargo, sealed holdout, CPCV
- [[baseline-checkpoint]] — narrow baseline như governance tool
- [[trial-taxonomy]] — strategy → trial family → trial → run
- [[strategy-term-sheet]] — structured strategy specification bằng dataclass
- [[cv-foundations]] — nền tảng CV cho time series

## Concepts mới (Chương 5 — Synthetic Data)

- [[generative-models-framework]] — phân loại mô hình sinh (VAE, GAN, diffusion, LLM)
- [[fidelity-utility-privacy]] — khuôn khổ đánh giá Fidelity-Utility-Privacy
- [[classical-simulation-baselines]] — bootstrap, GBM, jump-diffusion, Heston, GARCH
- [[financial-stylized-facts]] — 7 stylized facts của chuỗi lợi suất
- [[timegan]] — TimeGAN cho chuỗi thời gian tài chính
- [[tailgan-tail-risk]] — Tail-GAN và differentiable sorting
- [[sigcwgan]] — Signature-based CWGAN
- [[gtgan-irregular]] — GT-GAN + Neural ODE cho irregular timestamps
- [[diffusion-models-finance]] — Diffusion-TS với trend/seasonal decomposition
- [[llm-tabular-generators]] — GReaT cho dữ liệu bảng
- [[differential-privacy-generative]] — DP-GAN với Opacus

## Entities / Concepts khác

- [[stefan-jansen]]
- [[ml4t-library-ecosystem]]
- [[evidence-boundary]]
- [[deflated-sharpe-ratio]]

## Case Studies

- [[machine-learning-trading]] — về quy trình ML4T
- [[backtesting]] — backtesting event-driven
- [[quan-tri-rui-ro]] — quản trị rủi ro, stop-loss, kill switches

## Liên kết

- [../../raw/articles/chung-khoan/](../../raw/articles/chung-khoan/) (raw sources)
- [../../config.yaml](../../config.yaml) (cấu hình wiki)
