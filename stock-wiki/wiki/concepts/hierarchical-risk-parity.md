---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch17_06_hierarchical_risk_parity.py]
---

# Hierarchical Risk Parity (HRP)

A stability-first alternative to MVO that avoids covariance-matrix inversion pathologies entirely (López de Prado 2016).

## Steps

1. **Hierarchical clustering**: tree of asset relationships
2. **Quasi-diagonalization**: reorder covariance by cluster tree
3. **Recursive bisection**: allocate risk top-down through tree

## Advantages over MVO

- No matrix inversion → stable under high correlation
- Natural diversification structure
- Outperforms MVO out-of-sample in many settings
- Cluster interpretation (sector/industry exposure)

NB06 demonstrates on ETF data with Riskfolio-Lib and scipy clustering.

## Links

- [[portfolio-construction-ml]]
- [[mvo-robust-kelly]]
- [[conformal-position-sizing]]
- [[portfolio-evaluation-metrics]]
- [[feature-clustering]]

## Sources

- [ch17_06_hierarchical_risk_parity.py](../../raw/articles/chung-khoan/ch17_06_hierarchical_risk_parity.py)
