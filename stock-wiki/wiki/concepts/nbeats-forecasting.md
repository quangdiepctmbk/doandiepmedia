---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_02_nbeats_interpretable.py]
---

# N-BEATS for Financial Forecasting

N-BEATS (Neural Basis Expansion Analysis for Interpretable Time Series) decomposes forecasts into trend and seasonality components via stacked blocks, making it an interpretable deep learning alternative to black-box recurrent models.

## Key Ideas

- **Interpretable config**: explicit trend (monotonic basis) + seasonality (periodic basis) blocks
- **Generic config**: learnable basis without prior structure
- Each block fits residual of previous blocks (boosted decomposition)
- No feature engineering required — purely univariate

NB02 implements from scratch in PyTorch, demonstrating trend/seasonality decomposition on ETF data.

## Links

- [[dl-time-series-forecasting]]
- [[recurrent-architectures-lstm]]
- [[time-series-transformers]]

## Sources

- [ch13_02_nbeats_interpretable.py](../../raw/articles/chung-khoan/ch13_02_nbeats_interpretable.py)
