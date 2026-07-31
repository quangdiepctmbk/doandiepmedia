---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_10_uncertainty.py]
---

# DL Uncertainty Estimation (MC Dropout, Deep Ensembles)

Uncertainty estimation for deep learning time series models, enabling risk-aware position sizing.

## Methods

- **MC Dropout** (Gal & Ghahramani 2016): keep dropout active at inference, run N forward passes → distribution over predictions. Simple, zero additional parameters.
- **Deep Ensembles** (Lakshminarayanan et al. 2017): train N models with different seeds, ensemble → better uncertainty but N× training cost.

Both provide prediction intervals around point forecasts. NB10 implements both on LSTM + ETF data.

## Links

- [[dl-time-series-forecasting]]
- [[conformal-prediction-trading]]
- [[uncertainty-as-feature]]
- [[ml-pipeline-trading]]

## Sources

- [ch13_10_uncertainty.py](../../raw/articles/chung-khoan/ch13_10_uncertainty.py)
