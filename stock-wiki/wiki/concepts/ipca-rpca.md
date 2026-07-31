---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch14_04_ipca.py
  - raw/articles/chung-khoan/ch14_05_rp_pca.py
---

# IPCA & RP-PCA: Characteristic-Driven Latent Factors

Two extensions of PCA that make latent factor estimation more economically meaningful:

- **IPCA** (Instrumented PCA, Kelly-Pruitt-Su 2019): firm characteristics determine time-varying betas (βₜ = f(charₜ)). Betas = linear combination of characteristics.
- **RP-PCA** (Risk-Premium PCA, Lettau-Pelger 2020): objective = minimize pricing error (not variance). Penalizes factors that explain covariance but not expected returns.

Both move beyond "max variance" toward "economically relevant" factors.

## Links

- [[latent-factor-models]]
- [[pca-latent-factors]]
- [[conditional-autoencoder-asset-pricing]]
- [[feature-design-grammar]]

## Sources

- [ch14_04_ipca.py](../../raw/articles/chung-khoan/ch14_04_ipca.py)
- [ch14_05_rp_pca.py](../../raw/articles/chung-khoan/ch14_05_rp_pca.py)
