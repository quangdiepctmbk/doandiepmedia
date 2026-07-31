---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch15_README.md
ingested: 2026-07-26
related_raw:
  - ch15_01_library_overview.py
  - ch15_02_dowhy_causal_graph.py
  - ch15_03_econml_dml.py
  - ch15_04_dml_crypto_regime.py
  - ch15_05_momentum_causal_trading.py
  - ch15_06_fed_announcement_bsts.py
  - ch15_07_tigramite_time_series.py
  - ch15_08_neural_causal_discovery.py
  - ch15_09_adia_causal_benchmark.py
  - ch15_10_case_study_insights.py
  - ch15_11_factor_zoo_validation.py
---

# Causal Estimation — Chương 15 (ML4T)

## Summary

Chương 15 chuyển từ **predictive ML** sang **causal estimation** — thay vì hỏi "feature X có dự báo được return không?", hỏi "feature X có causal effect lên return không?". Ba questions, ba estimators:

1. **Continuous treatment effect** → Double Machine Learning (EconML)
2. **Discrete event impact** → Bayesian Structural Time-Series (BSTS / tfcausalimpact)
3. **Structure discovery** → PCMCI, NOTEARS, VAR-LiNGAM, Granger causality

11 notebooks + README:

- **NB01**: Library decision guide (EconML, DoWhy, CausalML, Tigramite, causal-learn)
- **NB02**: DoWhy validation workflow trên crypto funding rate
- **NB03**: DML momentum causal effect (ETF skip-recent 6-1)
- **NB04**: DML crypto premium z-score × volatility regimes
- **NB05**: CausalForestDML regime-conditional position sizing
- **NB06**: BSTS event study trên FOMC announcements (IEF Treasury ETF)
- **NB07**: PCMCI trên macro panel (GLD, IEF, SPY, VIX) — null result
- **NB08**: NOTEARS, VAR-LiNGAM, PCMCI, Granger comparison trên 7 ETFs
- **NB09**: ADIA Lab Causal Discovery Challenge reproduction
- **NB10**: Cross-case-study DML synthesis
- **NB11**: Factor zoo validation via double-selection LASSO

## Key Takeaways

- **DML** (Double Machine Learning) orthogonalizes treatment against confounders via cross-fitting
- **BSTS** constructs data-driven counterfactuals cho discrete events — but vulnerable to control spillover
- **Causal discovery** outputs are hypotheses, not truth — different methods give diverging edges
- **Confounding bias is pervasive** — naive OLS estimates shrink/disappear after DML
- **Predictive power ≠ causal effect** — a feature can predict returns without causing them
- **Refutation battery là mandatory**: placebo test, sensitivity analysis, subset stability

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 15
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/15_causal_estimation)
- [[ch14-latent-factors]] (previous chapter)
