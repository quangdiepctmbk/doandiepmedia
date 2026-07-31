---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch19_README.md]
---

# Risk Management for ML Trading

Risk management as system design: a strategy is not deployable until limits, escalation rules, and governance are defined in advance.

## Risk Pillars (Ch19)

- **Tail Risk**: VaR, CVaR — historical, parametric, Cornish-Fisher, backtested
- **Path Risk**: drawdown depth/duration, recovery time, MAE/MFE
- **Exposure Decomposition**: factor, sector, macro — intended vs accidental bets
- **Stress Testing**: historical crisis replay, hypothetical scenarios, reverse stress
- **Adaptive Controls**: vol targeting, exposure caps, position-level exits
- **Drift Monitoring**: detect when live distribution ≠ training distribution
- **Governance**: kill switches, escalation, written policies

## Key Principle

All controls must be leakage-safe — only information available at decision time.

## Links

- [[var-cvar-tail-risk]]
- [[drawdown-path-risk]]
- [[exit-strategies-stops]]
- [[mae-mfe-position-sizing]]
- [[factor-exposure-decomposition]]
- [[trade-shap-forensics]]
- [[stress-testing-scenarios]]
- [[drift-detection-monitoring]]
- [[ml-exit-signals]]
- [[deep-hedging]]
- [[risk-systematic-sweep]]
- [[kill-switch-governance]]
- [[ml4t-risk-library]]
- [[ml-backtest-baseline]]

## Sources

- [ch19_README.md](../../raw/articles/chung-khoan/ch19_README.md)
- [[ch19-risk-management]]
