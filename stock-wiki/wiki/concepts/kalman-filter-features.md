---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_04_kalman_filter.py, ch09_README.md]
---

# Kalman Filter Features

Kalman filter as a production feature extractor — recovered latent state và innovation signals from noisy price series.

## Local Linear Trend Model

State vector: [level, slope]
- **Level**: smoothed price estimate
- **Trend**: slope / trend direction
- **Update**: prediction → observation → correction (Kalman gain)

## Four Production Features

| Feature | Description | Use Case |
|---------|-------------|----------|
| `kalman_level` | Smoothed price estimate | Price trend signal |
| `kalman_trend` | Slope (trend direction) | Momentum signal |
| `kalman_innovation` | Prediction surprise | Mean reversion signal |
| `kalman_uncertainty` | State variance (P matrix diagonal) | Position sizing |

## Dynamic Hedge Ratio

Kalman filter ước lượng time-varying beta cho pairs trading — beats rolling OLS khi beta thay đổi dần dần.

- State: [intercept, slope]
- Observation: y = α + β·x + ε
- Innovation = y_pred - y_obs → mean reversion signal

## MLE Noise Covariance Estimation

Estimate observation noise (R) và state transition noise (Q) via MLE — adapts to recent volatility.

## Comparison

Kalman filter beats EMA và rolling OLS on IC (Information Coefficient) cho hedge ratio estimation.

## Sources

- [ch09_04_kalman_filter.py](../../raw/articles/chung-khoan/ch09_04_kalman_filter.py)
- [[model-based-feature-extraction]]
- [[panel-temporal-features]]
