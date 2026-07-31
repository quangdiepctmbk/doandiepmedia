---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_01_core_architectures.py]
---

# Recurrent Architectures (LSTM/GRU) for Financial Time Series

Core recurrent architectures — LSTM and GRU — addressed vanishing gradients in vanilla RNNs via gating mechanisms, making them the historical baseline for sequential financial data.

## Tradeoffs (NB01)

NB01 compares MLP, 1D-CNN, LSTM, GRU on ETF return prediction:

- **LSTM/GRU > MLP/CNN** for sequence tasks — temporal structure matters
- **LSTM ≈ GRU** in accuracy, GRU slightly faster (fewer gates)
- **Sequential compute bottleneck**: can't parallelize across time steps
- **Struggle with very long dependencies** despite gates

This bottleneck motivated every later architecture: N-BEATS (structured), Transformers (attention), TCN (parallel conv), Mamba (linear SSM).

## Links

- [[dl-time-series-forecasting]]
- [[nbeats-forecasting]]
- [[time-series-transformers]]
- [[mamba-ssm-finance]]

## Sources

- [ch13_01_core_architectures.py](../../raw/articles/chung-khoan/ch13_01_core_architectures.py)
