---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_01_ols_inference.py
---

# OLS Inference to Prediction

The transition from classical OLS inference (unbiased coefficient estimation, p-values, Gauss-Markov assumptions) to predictive modeling (stable OOS forecasts, shrinkage, cross-validation).

## Why OLS is Not Enough for Trading

- Features are numerous, correlated, and noisy → OLS overfits
- Coefficient recovery is not the goal — signal stability is
- Market non-stationarity violates Gauss-Markov assumptions
- Shrinkage (Ridge) trades bias for variance reduction

NB01 demonstrates the full inferential toolkit on ETF data before departing for regularized methods.

## Links

- [[regularized-regression-trading]]
- [[ml-pipeline-trading]]
- [[train-only-preprocessing]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_01_ols_inference.py](../../raw/articles/chung-khoan/ch11_01_ols_inference.py)
