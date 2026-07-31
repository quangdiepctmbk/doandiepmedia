---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_03_structural_cross_instrument_features.py]
---

# Structural and Cross-Instrument Features

Features xuất hiện từ quan hệ giữa các contract, asset và derivative market — không thể tính từ một price series duy nhất.

## Feature Families

- **Carry & Term Structure**: roll yield (futures), term structure slope/curvature
- **Cross-Asset Relative Value**: rolling beta to market, beta-adjusted residual momentum, lead-lag correlations, deviation from peer mean (relative value z-score)
- **Options-Implied**: ATM implied volatility, risk reversal (25-delta skew), IV term structure slope, variance risk premium (IV - RV)

## Key Constraints

- Maturity alignment (future contract expiry)
- Peer-set definition (universe và benchmark)
- Surface policy (which option strikes/tenors)

## Links

- [[price-volume-features]]
- [[slow-moving-contextual-features]]
- [[feature-design-grammar]]

## Sources

- [Structural/cross-instrument source](../../raw/articles/chung-khoan/ch08_03_structural_cross_instrument_features.py)
