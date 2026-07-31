---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_14_panel_features.py, ch09_case_study_temporal_summary.py, ch09_README.md]
---

# Panel and Temporal Features

Cross-sectional transforms và pairwise relationships — bridge từ single-asset temporal models đến multi-asset prediction và portfolio construction.

## Cross-Sectional Ranking

Sort temporal features (volatility, trend, momentum) across universe → decile/percentile features:

- `vol_decile` — relative volatility rank
- `trend_percentile` — relative trend strength
- `z_score_relative` — cross-sectional z-score

## Relative Temporal Features

Benchmark-adjusted: `ret_vs_spy = ret - ret_spy`, `sector_relative = feature - sector_median`

## Cointegration

- **Engle-Granger**: two-step — OLS spread → ADF on residuals (single pair)
- **Johansen**: VECM — trace test for cointegration rank (multiple pairs)
- **Static hedge ratio** (OLS): h = cov/var
- **Dynamic hedge ratio** (Kalman filter): time-varying β

## Ornstein-Uhlenbeck Half-Life

Mean-reversion speed measure: `half_life = ln(2) / |θ|` (θ = O-U speed parameter, estimated by OLS on spread changes).

Half-life < N days → candidate for pairs trading.

## Multi-Asset Regime Aggregation

Temporal regime probabilities aggregated cross-sectionally:

- % assets in each regime → market-wide regime signal
- Regime dispersion — disagreement measure
- Regime transition synchrony

## Case Study Temporal Summary

`case_study_temporal_summary.py` collects all temporal features from all case studies into a unified table showing which models run in which notebooks.

## Sources

- [ch09_14_panel_features.py](../../raw/articles/chung-khoan/ch09_14_panel_features.py)
- [[model-based-feature-extraction]]
- [[kalman-filter-features]]
- [[regime-features]]
- [[price-volume-features]]
