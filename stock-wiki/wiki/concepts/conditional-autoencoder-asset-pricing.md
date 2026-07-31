---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch14_06_conditional_autoencoder.py]
---

# Conditional Autoencoder for Asset Pricing

Conditional Autoencoder (CAE, Gu-Kelly-Xiu 2019) learns **nonlinear latent factors** from returns and firm characteristics simultaneously via an autoencoder architecture.

## Architecture

- **Encoder**: compresses returns → latent factors (nonlinear)
- **Decoder**: reconstructs returns from latent factors + characteristics
- **Characteristics as conditioning variables**: firm-level features (size, value, momentum, etc.) determine factor loadings

## Workflow (NB06)

- Universe construction on US equities
- Walk-forward training with expanding windows
- Ensemble averaging across random seeds
- SHAP-based interpretation of characteristic → factor mapping

## Links

- [[latent-factor-models]]
- [[stochastic-discount-factor-dl]]
- [[dl-time-series-forecasting]]
- [[walk-forward-evaluation]]

## Sources

- [ch14_06_conditional_autoencoder.py](../../raw/articles/chung-khoan/ch14_06_conditional_autoencoder.py)
