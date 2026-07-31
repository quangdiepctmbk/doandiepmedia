---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch14_09_case_study_insights.py]
---

# Latent Factor Case Study Insights

Marchenko-Pastur dimensionality diagnostic applied to all 9 ML4T case studies: hầu hết datasets không đủ cross-sectional breadth cho latent factor extraction.

## Key Finding

- **Yield curve**: 3 factors (level, slope, curvature) — textbook success
- **Sector ETFs**: market + rotation factors — latent factors work
- **US equities (3,199 stocks)**: eigenportfolios and CAE viable
- **Other datasets (crypto, FX, futures)**: insufficient breadth → latent factors unreliable

The negative finding is the chapter's most practical insight: don't use latent factor models on narrow cross-sections.

## Links

- [[latent-factor-models]]
- [[pca-latent-factors]]
- [[conditional-autoencoder-asset-pricing]]
- [[ml-backtest-baseline]]

## Sources

- [ch14_09_case_study_insights.py](../../raw/articles/chung-khoan/ch14_09_case_study_insights.py)
