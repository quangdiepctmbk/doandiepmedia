---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch19_01_var_cvar.py
  - raw/articles/chung-khoan/ch19_02_exit_strategies.py
  - raw/articles/chung-khoan/ch19_03_position_sizing_mae_mfe.py
---

# VaR, CVaR & Path Risk

Tail risk measurement and path-dependent drawdown analysis.

## VaR/CVaR (NB01)

- Historical, parametric (normal), Cornish-Fisher (adjusts skew/kurtosis)
- Backtest VaR violations (exceedance rate)
- Regime-conditional and liquidity-aware estimates

## Drawdown & Path Risk (NB02-03, NB10)

- Drawdown depth, duration, recovery time
- Exit strategies: fixed stops, trailing stops, vol-adjusted, hybrid
- MAE/MFE: Maximum Adverse/Favorable Excursion → calibrate stop placement
- Volatility-based position sizing

NB10 demonstrates ml4t.backtest.risk: production-ready stop-loss rules, rule composition, kill switches.

## Links

- [[risk-management-ml]]
- [[stress-testing-scenarios]]
- [[drift-detection-monitoring]]
- [[ml4t-risk-library]]

## Sources

- [ch19_01_var_cvar.py](../../raw/articles/chung-khoan/ch19_01_var_cvar.py)
- [ch19_02_exit_strategies.py](../../raw/articles/chung-khoan/ch19_02_exit_strategies.py)
- [ch19_03_position_sizing_mae_mfe.py](../../raw/articles/chung-khoan/ch19_03_position_sizing_mae_mfe.py)
- [ch19_10_ml4t_backtest_risk_demo.py](../../raw/articles/chung-khoan/ch19_10_ml4t_backtest_risk_demo.py)
- [ch19_11_systematic_risk_sweep.py](../../raw/articles/chung-khoan/ch19_11_systematic_risk_sweep.py)
