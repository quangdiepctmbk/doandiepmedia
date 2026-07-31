---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch17_07_conformal_position_sizing.py]
---

# Conformal Position Sizing

Uses conformal prediction intervals to scale positions: wider uncertainty → smaller size.

## Two Case Studies (NB07)

- **ETFs**: conformal weighting improves Sharpe +5.5%
- **CME Futures**: degrades Sharpe -24.8% → conformal benefits are context-dependent

Key: conformal sizing works when prediction intervals reflect genuine uncertainty; fails when intervals are poorly calibrated for the asset class.

## Links

- [[portfolio-construction-ml]]
- [[conformal-prediction-trading]]
- [[conformal-prediction-gbm]]
- [[mvo-robust-kelly]]
- [[dl-uncertainty-estimation]]

## Sources

- [ch17_07_conformal_position_sizing.py](../../raw/articles/chung-khoan/ch17_07_conformal_position_sizing.py)
