---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch13_05_tcn.py
  - raw/articles/chung-khoan/ch13_06_tsmixer.py
  - raw/articles/chung-khoan/ch13_07_mamba_ssm.py
  - raw/articles/chung-khoan/ch13_08_cnn_image_encoding.py
---

# Alternative TS Architectures: TCN, TSMixer, Mamba, CNN Encoding

Survey of non-Transformer, non-recurrent architectures for time series:

- **TCN** (Temporal Convolutional Network): dilated causal convolutions — parallel (unlike LSTM), limited very-long-range
- **TSMixer** (Google 2023): MLP-only — alternating time-mixing (temporal patterns) × feature-mixing (cross-variate interactions). Competitive with attention.
- **Mamba SSM** (Gu & Dao 2023): structured state space model — O(T) vs O(T²), selective state spaces. FinMamba (Hu et al. 2025) for stock prediction.
- **CNN Image Encoding** (GAF/MTF): convert TS to 2D images → classify with CNN. Gramian Angular Fields + Markov Transition Fields encode temporal structure visually.

## Links

- [[dl-time-series-forecasting]]
- [[time-series-transformers]]
- [[ts-mixer-model]]

## Sources

- [ch13_05_tcn.py](../../raw/articles/chung-khoan/ch13_05_tcn.py)
- [ch13_06_tsmixer.py](../../raw/articles/chung-khoan/ch13_06_tsmixer.py)
- [ch13_07_mamba_ssm.py](../../raw/articles/chung-khoan/ch13_07_mamba_ssm.py)
- [ch13_08_cnn_image_encoding.py](../../raw/articles/chung-khoan/ch13_08_cnn_image_encoding.py)
