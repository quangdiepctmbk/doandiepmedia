---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch13_README.md
ingested: 2026-07-26
related_raw:
  - ch13_01_core_architectures.py
  - ch13_02_nbeats_interpretable.py
  - ch13_03_great_debate.py
  - ch13_04_transformers.py
  - ch13_05_tcn.py
  - ch13_06_tsmixer.py
  - ch13_07_mamba_ssm.py
  - ch13_08_cnn_image_encoding.py
  - ch13_09_foundation_models.py
  - ch13_10_uncertainty.py
  - ch13_11_library_landscape.py
  - ch13_12_case_study_insights.py
  - ch13_dl_sequences.py
---

# Deep Learning for Time Series — Chương 13 (ML4T)

## Summary

Chương 13 tổng quan **deep learning architectures cho time series forecasting trong trading**, từ recurrent networks (LSTM/GRU) đến modern alternatives: N-BEATS, Transformers (PatchTST, iTransformer, TFT), TCN, TSMixer, Mamba SSM, và foundation models (Chronos, Moirai, TTM). Kết luận chính: DL thắng rõ trên một phần narrow của evidence base, baselines đơn giản vẫn rất khó beat.

13 notebooks + 1 shared module (`dl_sequences.py`):

1. **13.1 Recurrent Paradigm** — MLP / 1D-CNN / LSTM / GRU comparison
2. **13.2 N-BEATS** — Decomposition-based, trend + seasonality
3. **13.3 Attention Revolution** — Transformers cho time series
4. **13.4 The Great Debate** — Zeng et al. critique: simple linear beat many Transformers
5. **13.5 Transformer Evolution** — PatchTST, iTransformer, TFT
6. **13.6 Full Toolkit** — TCN, TSMixer, Mamba SSM, CNN image encoding, foundation models
7. **13.7 Practitioner's Framework** — khi nào dùng DL, khi nào dùng panel regression
8. **13.8 Uncertainty** — MC Dropout, Deep Ensembles
9. **13.9 Cross-Dataset Insights** — DL thắng narrow band, tabular baselines hard to dislodge

## Key Takeaways

- **LSTM/GRU > MLP/CNN** cho sequence tasks, nhưng sequential compute bottleneck
- **N-BEATS**: interpretable trend/seasonality decomposition — like a disciplined forecaster
- **The Great Debate**: simple linear baselines embarrass many Transformer variants (Zeng et al. 2022). Modern TS Transformers (PatchTST, iTransformer) overcome this
- **PatchTST**: patching along time axis — local temporal patterns
- **iTransformer**: attention over features — cross-variate dependence
- **TCN > LSTM** in speed (parallel convolutions) but limited very-long-range
- **TSMixer**: MLP-only, time-mixing × feature-mixing — competitive with no attention
- **Mamba SSM**: O(T) vs O(T²), selective state spaces, promising for long sequences
- **Foundation models** (Chronos, TTM, Moirai): zero-shot transfer — transfer gap for finance (Rahimikia et al. 2025)
- **Uncertainty**: MC Dropout + Deep Ensembles cho position sizing
- **Bottom line**: DL không phải magic bullet. Table baseline trước, model complexity chỉ hợp lý khi simple baselines đã chạm ceiling

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 13
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/13_dl_time_series)
- [[ch12-gradient-boosting]] (previous chapter)
