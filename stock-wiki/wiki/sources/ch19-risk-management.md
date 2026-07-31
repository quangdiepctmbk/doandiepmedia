---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch19_README.md
ingested: 2026-07-26
related_raw:
  - ch19_01_var_cvar.py
  - ch19_02_exit_strategies.py
  - ch19_03_position_sizing_mae_mfe.py
  - ch19_04_factor_exposure.py
  - ch19_05_trade_shap_diagnostics.py
  - ch19_06_stress_testing.py
  - ch19_07_drift_detection.py
  - ch19_08_ml_exit_signals.py
  - ch19_09_deep_hedging.py
  - ch19_10_ml4t_backtest_risk_demo.py
  - ch19_11_systematic_risk_sweep.py
---

# Risk Management — Chương 19 (ML4T)

## Summary

Chương 19 reframes risk management từ post hoc reporting thành **system design**: a strategy is not deployable until limits, escalation rules, and governance are defined in advance.

11 notebooks + README. 8 sections.

### Sections:

1. **19.1 Risk in ML4T Workflow**: deployability requires advance-defined limits
2. **19.2 Risk Taxonomy**: market, factor, leverage, concentration, liquidity, model, operational risk
3. **19.3 VaR & CVaR**: tail risk measurement — historical, parametric, Cornish-Fisher, backtesting (NB01)
4. **19.4 Drawdowns & Path Risk**: depth, duration, recovery time; exit strategies (NB02), MAE/MFE stops (NB03), ml4t.backtest.risk (NB10)
5. **19.5 Factor Exposure Decomposition**: intended vs unintended bets; TradeSHAP forensics (NB04-05)
6. **19.6 Stress Testing**: historical crisis replay, hypothetical scenarios, reverse stress tests (NB06)
7. **19.7 Adaptive Risk Controls**: vol targeting, exposure caps, drift detection (NB07), ML exit signals (NB08), deep hedging (NB09), systematic sweep (NB11)
8. **19.8 Kill Switches & Governance**: written governance, drift monitoring, escalation

### Key Takeaways

- **VaR alone never enough** — CVaR, regime-conditional, liquidity-aware tail estimates essential
- **Path risk** (drawdown depth/duration) kills strategies as much as total loss
- **Factor exposure decomposition** reveals intended vs accidental bets
- **Stress testing**: historical crisis replay + hypothetical shock matrices
- **Adaptive controls**: vol targeting, caps, stops — must be leakage-safe
- **Drift detection**: when live distribution ≠ training distribution, models silently degrade
- **Deep hedging** (Buehler et al. 2019): NN learns hedging positions minimizing CVaR under costs
- **Kill switches**: pre-defined failure conditions + escalation ladder

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 19
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/19_risk_management)
- [[ch18-transaction-costs]] (previous chapter)
