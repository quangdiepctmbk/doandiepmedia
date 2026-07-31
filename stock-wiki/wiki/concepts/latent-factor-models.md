---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch14_README.md]
---

# Latent Factor Models

Latent factor models extract lower-dimensional risk structure directly from returns, bypassing the "factor zoo" problem of choosing among hundreds of named factors.

## Key Distinction

- **Attribution factors**: explain return covariance (what moves together)
- **Priced factors**: explain expected returns (what earns risk premia)

This distinction threads the entire chapter: PCA finds attribution factors; SDF methods price factors; CAE does both nonlinearly.

## Methods Span

| Method | Objective | Key Reference |
|--------|-----------|--------------|
| PCA | Max variance | Classic |
| Eigenportfolios | PCA weights → portfolio | Avellaneda & Lee 2010 |
| IPCA | Characteristic-driven betas | Kelly-Pruitt-Su 2019 |
| RP-PCA | Min pricing error | Lettau-Pelger 2020 |
| CAE | Nonlinear latent factors | Gu-Kelly-Xiu 2019 |
| Adversarial SDF | No-arbitrage pricing | Chen-Pelger-Zhu 2021 |
| Supervised AE | Reconstruction + prediction | Jane Street Kaggle |

## Links

- [[pca-latent-factors]]
- [[eigenportfolios]]
- [[ipca-model]]
- [[rp-pca-model]]
- [[conditional-autoencoder-asset-pricing]]
- [[stochastic-discount-factor-dl]]
- [[ml-pipeline-trading]]

## Sources

- [ch14_README.md](../../raw/articles/chung-khoan/ch14_README.md)
- [[ch14-latent-factors]]
