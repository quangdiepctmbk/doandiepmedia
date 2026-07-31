---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_README.md]
---

# Deep Learning for Time Series Forecasting

Survey of deep learning architectures for time series in trading — từ recurrent networks đến modern alternatives, với insight rằng simple baselines khó beat và DL chỉ thắng trong narrow band.

## Architecture Buckets

- **Recurrent**: LSTM, GRU — sequential bottleneck, vanishing gradient
- **Decomposition**: N-BEATS — trend + seasonality blocks
- **Attention**: Transformers (PatchTST, iTransformer, TFT) — patching / feature attention
- **Convolutional**: TCN — dilated causal conv, parallel
- **MLP-only**: TSMixer — time-mixing × feature-mixing
- **State Space**: Mamba SSM — O(T) selective state spaces
- **Image Encoding**: GAF/MTF → CNN — treat TS as image
- **Foundation Models**: Chronos, TTM, Moirai — zero-shot pretrained TS models
- **Uncertainty**: MC Dropout, Deep Ensembles

## Practitioner's Framework

- Establish baseline ladder: Ridge → GBM → simple DL → advanced DL
- Diagnose problem: horizon, multivariate structure, covariates
- DL complexity only justified when simple baselines hit ceiling

## Links

- [[recurrent-architectures-lstm]]
- [[nbeats-forecasting]]
- [[time-series-transformers]]
- [[mamba-ssm-finance]]
- [[ts-mixer-model]]
- [[time-series-foundation-models]]
- [[dl-uncertainty-estimation]]
- [[ml-backtest-baseline]]

## Sources

- [ch13_README.md](../../raw/articles/chung-khoan/ch13_README.md)
- [[ch13-dl-time-series]]
