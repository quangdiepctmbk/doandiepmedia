---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch17_README.md]
---

# Portfolio Construction for ML Trading

Frames allocation as combining expected returns, covariance, constraints, leverage, and rebalancing into actual weights. Small allocation decisions amplify or destroy edge.

## Hierarchy of Allocators

1. **Simple Baselines**: equal weight, inverse volatility, score weighting, risk parity
2. **MVO**: mean-variance with shrinkage + constraints (Markowitz Curse)
3. **Robust Optimization**: min variance, min CVaR, Riskfolio-Lib (NB03)
4. **Kelly Criterion**: log-growth principle, fractional Kelly (NB04)
5. **HRP**: hierarchical clustering → quasi-diagonalization → recursive bisection (NB06)
6. **Regime-Adaptive**: conformal sizing (NB07), DL portfolio (NB11-13)
7. **End-to-End DL**: bypass predict-then-optimize, pooled-Sharpe loss

## Key Metrics (NB01)

Sharpe, IR, active share, HHI concentration, risk contributions, leverage stability, drawdown regime-slice.

## Links

- [[mean-variance-optimization]]
- [[kelly-criterion-sizing]]
- [[hierarchical-risk-parity]]
- [[conformal-position-sizing]]
- [[dl-portfolio-allocation]]
- [[vlstm-portfolio]]
- [[deepm-regime-robust]]
- [[allocator-comparison-protocol]]
- [[portfolio-evaluation-metrics]]
- [[ml-backtest-baseline]]

## Sources

- [ch17_README.md](../../raw/articles/chung-khoan/ch17_README.md)
- [[ch17-portfolio-construction]]
