---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_06_conformal_prediction.py
---

# Conformal Prediction for Trading

Conformal prediction generates prediction intervals with finite-sample valid coverage under minimal assumptions (exchangeability). For trading, this connects raw forecasts to risk-aware position sizing.

## Methods in Ch11

- **Split-conformal**: simplest, single calibration split
- **Adaptive conformal inference**: adapts to distribution shift
- **Conformalized quantile regression (CQR)**: intervals that adapt to feature-dependent uncertainty

## Financial Caveat

Financial data violates exchangeability (non-stationary, regime-dependent). Conformal coverage must be monitored: when coverage degrades, the model is either drifting or the market regime has changed.

## Links

- [[ml-pipeline-trading]]
- [[ml-backtest-baseline]]
- [[uncertainty-as-feature]]
- [[regime-features]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_06_conformal_prediction.py](../../raw/articles/chung-khoan/ch11_06_conformal_prediction.py)
