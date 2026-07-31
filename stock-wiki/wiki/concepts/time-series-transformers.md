---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch13_README.md
  - raw/articles/chung-khoan/ch13_04_transformers.py
---

# Time Series Transformers (PatchTST, iTransformer)

Modern Transformer variants for time series, designed to address the "Great Debate" critiques:

- **PatchTST**: patching along time dimension — groups consecutive time steps into patches, reducing sequence length and capturing local temporal patterns
- **iTransformer**: attention over features (not time) — models cross-variate dependencies while using simple MLP for temporal processing
- **TFT (Temporal Fusion Transformer)**: covariate-rich forecasting with interpretable attention

All use walk-forward evaluation on ETF 21-day forward returns. NB04 compares PatchTST vs iTransformer.

## Links

- [[dl-time-series-forecasting]]
- [[ts-great-debate]]
- [[ts-mixer-model]]
- [[mamba-ssm-finance]]
- [[walk-forward-evaluation]]

## Sources

- [ch13_04_transformers.py](../../raw/articles/chung-khoan/ch13_04_transformers.py)
