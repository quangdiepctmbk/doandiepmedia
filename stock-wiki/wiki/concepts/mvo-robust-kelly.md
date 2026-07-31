---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch17_02_mean_variance_optimization.py
  - raw/articles/chung-khoan/ch17_03_robust_optimization.py
  - raw/articles/chung-khoan/ch17_04_kelly_criterion.py
---

# Mean-Variance, Robust Optimization & Kelly Criterion

Three canonical allocation frameworks with different assumptions and fragility.

## Mean-Variance (Markowitz)

- **Curse**: noisy expected returns + unstable covariance → extreme weights
- **Fixes**: shrinkage (Ledoit-Wolf), constraints, factor structure

## Robust Optimization (NB03)

- Risk parity, min variance, min CVaR
- Riskfolio-Lib library
- Less weight sensitivity than MVO

## Kelly Criterion (NB04)

- Optimal f* for log-growth
- Full Kelly impractical (concentration risk + volatility)
- Fractional Kelly (1/2, 1/4 Kelly) safer
- Multi-asset extension via covariance

## Links

- [[portfolio-construction-ml]]
- [[portfolio-evaluation-metrics]]
- [[hierarchical-risk-parity]]
- [[conformal-position-sizing]]
- [[asset-allocation-theory]]

## Sources

- [ch17_02_mean_variance_optimization.py](../../raw/articles/chung-khoan/ch17_02_mean_variance_optimization.py)
- [ch17_03_robust_optimization.py](../../raw/articles/chung-khoan/ch17_03_robust_optimization.py)
- [ch17_04_kelly_criterion.py](../../raw/articles/chung-khoan/ch17_04_kelly_criterion.py)
