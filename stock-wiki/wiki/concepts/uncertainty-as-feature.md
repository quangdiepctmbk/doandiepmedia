---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_10_uncertainty_features.py, ch09_README.md]
---

# Uncertainty as Feature

Model's uncertainty is itself informative — posterior widths, forecast standard errors, interval widths.

## Principle

Signal strength, sizing, and interpretation nên phụ thuộc không chỉ vào predicted value mà còn vào **how confident the model is**. Two identical point forecasts với different uncertainty levels imply different position sizing.

## Walk-Forward Stochastic Volatility Model

Bayesian SV model fit within expanding windows:

1. Fit PyMC NUTS sampler trên training window
2. Extract posterior distributions: vol_posterior_std, vol_ci_width, vol_of_vol, vol_persistence
3. Generate **out-of-sample vol posterior** cho next window

### MCMC Diagnostics

- R-hat < 1.01: convergence (Gelman-Rubin)
- ESS > 400: effective sample size
- NUTS sampling: 3 min per fit (PyMC trên laptop)

## ARIMA Forecast Uncertainty

Nixtla `statsforecast` với AutoARIMA:

- Forecast standard errors từ residual variance
- 95% prediction interval width
- Conformal prediction adjustment (Sun & Yu 2025)

## Production Notes

- Retrain weekly (not daily) để balance cost vs refresh
- Use **conformal prediction** cho calibration-robust intervals
- Combine: posterior width + ARIMA interval + rolling residual std

## Sources

- [ch09_10_uncertainty_features.py](../../raw/articles/chung-khoan/ch09_10_uncertainty_features.py)
- [[model-based-feature-extraction]]
- [[volatility-model-features]]
