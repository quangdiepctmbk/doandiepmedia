---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch14_01_pca_equity_sectors.py
  - raw/articles/chung-khoan/ch14_02_eigenportfolios.py
  - raw/articles/chung-khoan/ch14_03_yield_curve_decomposition.py
---

# PCA for Financial Factor Extraction

PCA extracts latent risk factors from return covariance. Despite simplicity, it remains the baseline for latent factor modeling.

## Key Applications (Ch14)

- **Sector ETFs** (NB01): PCA captures market + rotation factors. Loading stability diagnosed via bootstrap resampling.
- **US Equities** (NB02): 3,199 stocks → eigenportfolios, sector loading analysis, hierarchical PCA (HPCA), stat-arb, risk decomposition.
- **Yield Curve** (NB03): Level / Slope / Curvature explain most yield-curve variation. Textbook success story.

## Practical Issues

- Noisy covariance estimation in high dimensions
- Variance extraction ≠ pricing relevance
- Loadings unstable over time
- Top PCs explain covariance well but may not be priced

## Links

- [[latent-factor-models]]
- [[eigenportfolios]]
- [[ipca-model]]
- [[rp-pca-model]]
- [[conditional-autoencoder-asset-pricing]]

## Sources

- [ch14_01_pca_equity_sectors.py](../../raw/articles/chung-khoan/ch14_01_pca_equity_sectors.py)
- [ch14_02_eigenportfolios.py](../../raw/articles/chung-khoan/ch14_02_eigenportfolios.py)
- [ch14_03_yield_curve_decomposition.py](../../raw/articles/chung-khoan/ch14_03_yield_curve_decomposition.py)
