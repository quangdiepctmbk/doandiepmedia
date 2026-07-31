---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch14_02_eigenportfolios.py]
---

# Eigenportfolios

PCA eigenvectors interpreted as **portfolio weights**: the top principal components define long-short portfolios that capture dominant risk dimensions in the equity cross-section.

## Applications

- **Statistical arbitrage**: eigenportfolios as mean-reversion trading signals
- **Risk decomposition**: attributing portfolio risk to latent factors
- **Sector exposure analysis**: via hierarchical PCA (HPCA, Avellaneda 2019)

## Practical Concerns

- Loading instability over time
- Production stabilization needed (rolling windows, shrinkage)
- Interpretability of eigenportfolio weights

NB02 applies PCA + HPCA on 3,199 US equities from the ML4T dataset.

## Links

- [[latent-factor-models]]
- [[pca-latent-factors]]
- [[ipca-model]]
- [[rp-pca-model]]

## Sources

- [ch14_02_eigenportfolios.py](../../raw/articles/chung-khoan/ch14_02_eigenportfolios.py)
