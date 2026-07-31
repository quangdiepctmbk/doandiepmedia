---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch14_07_stochastic_discount_factor.py
  - raw/articles/chung-khoan/ch14_08_supervised_autoencoder.py
---

# Stochastic Discount Factor & Supervised Autoencoder

Two deep learning approaches that go beyond reconstruction to incorporate pricing constraints:

- **Adversarial SDF** (Chen-Pelger-Zhu 2021): adversarial moment-based estimator that enforces no-arbitrage restrictions via a GMM-style objective. Objective = pricing error (not reconstruction loss). Uses macro instruments.
- **Supervised Autoencoder** (Jane Street Kaggle 2020-21): shared encoder with 3-loss objective: (1) reconstruction, (2) auxiliary prediction, (3) main prediction. Applied to US equities in NB08. GPU ~20 min.

## Links

- [[latent-factor-models]]
- [[conditional-autoencoder-asset-pricing]]
- [[ml-pipeline-trading]]
- [[ipca-rpca]]

## Sources

- [ch14_07_stochastic_discount_factor.py](../../raw/articles/chung-khoan/ch14_07_stochastic_discount_factor.py)
- [ch14_08_supervised_autoencoder.py](../../raw/articles/chung-khoan/ch14_08_supervised_autoencoder.py)
