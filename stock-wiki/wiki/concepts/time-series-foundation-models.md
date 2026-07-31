---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_09_foundation_models.py]
---

# Time Series Foundation Models

Time Series Foundation Models (TSFMs) are pretrained on diverse time series data and adapted to financial forecasting with zero-shot or few-shot transfer.

## Models in Ch13

- **Chronos** (Amazon): pretrained on 100M+ TS from multiple domains
- **TTM** (IBM): tiny time mixers, efficient few-shot
- **Moirai-MoE** (Salesforce): mixture-of-experts TS foundation model

## Transfer Gap

Rahimikia et al. (2025) show TSFMs face a **financial transfer gap**: pretraining on general TS data does not guarantee good performance on financial data. Key issues:

- Distribution shift between pretraining and financial data
- Pretraining contamination (data leakage)
- Zero-shot often worse than simple baselines on financial tasks

NB09 evaluates Chronos/TTM zero-shot + LSTM baseline on ETF returns — does transfer pretraining help?

## Links

- [[dl-time-series-forecasting]]
- [[alternative-ts-architectures]]
- [[ml-backtest-baseline]]
- [[regularized-regression-trading]]

## Sources

- [ch13_09_foundation_models.py](../../raw/articles/chung-khoan/ch13_09_foundation_models.py)
