---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_01_price_volume_features.py]
---

# Price/Volume Features

Feature families derived from a single asset's price and volume history. Là workhorse features — available cho mọi tradeable instrument.

## Families Covered

- **Returns & Horizons**: raw returns, skip-1 momentum, session-based returns
- **Trend & Reversal**: MA distance (vol-scaled), rolling regression slope, short-term reversal, distance to MA in ATR units
- **Volatility**: close-to-close RV, range-based (Parkinson, Garman-Klass, Yang-Zhang, Rogers-Satchell), vol-of-vol, volatility state features, price-derived regime indicators
- **Volume & Liquidity**: dollar volume, relative volume, VWAP distance
- **Cross-Sectional Normalization**: cross-sectional ranks, vol-scaled CS momentum, CS z-scores (point-in-time discipline)
- **Risk Features**: drawdown, max drawdown, ulcer index
- **ML-Specific Transforms**: interactions, polynomial expansions

## Key Rule

Cross-sectional normalization (rank/z-score) luôn phải là point-in-time — không dùng future data để tính quantile.

## Links

- [[microstructure-features]]
- [[structural-cross-instrument-features]]
- [[feature-design-grammar]]
- [[feature-selection-dedup]]

## Sources

- [Price/volume features source](../../raw/articles/chung-khoan/ch08_01_price_volume_features.py)
