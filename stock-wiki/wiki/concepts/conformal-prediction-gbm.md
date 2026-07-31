---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_11_conformal_gbm.py]
---

# Conformal Prediction for GBMs

Conformal prediction intervals cho GBM regression: split-conformal, conformalized quantile regression (CQR), và quantile regression–based conformal prediction.

## Why It Matters

GBMs produce **point predictions** without built-in uncertainty. Conformal prediction adds:

- Finite-sample valid coverage (under exchangeability)
- Adaptive intervals via CQR (feature-dependent width)
- Coverage diagnostics for non-exchangeable financial data

NB11 extends Ch11's conformal workflow from linear models to tree ensembles.

## Links

- [[gradient-boosting-trading]]
- [[conformal-prediction-trading]]
- [[uncertainty-as-feature]]
- [[ml-backtest-baseline]]

## Sources

- [ch12_11_conformal_gbm.py](../../raw/articles/chung-khoan/ch12_11_conformal_gbm.py)
