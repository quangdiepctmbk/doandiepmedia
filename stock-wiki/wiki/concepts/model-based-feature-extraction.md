---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_README.md]
---

# Model-Based Feature Extraction

Model-based feature extraction là cách dùng output của một fitted statistical/ML procedure làm input features cho downstream trading models.

## Definition

Khác với direct features (rolling mean, momentum, ratios), model-based features cần fit một model hoặc diagnostic procedure trên historical window rồi lấy outputs như:

- forecasts
- residuals
- filtered states
- conditional volatility
- regime probabilities
- uncertainty intervals
- break statistics

## Point-in-Time Rule

Chương 9 nhấn mạnh mọi fitted procedure phải được fit/select **inside training windows**. Production-safe features dùng filtered/one-sided outputs, không dùng smoothed/future-informed outputs.

## Common Feature Families

- [[stationarity-diagnostic-features]]
- [[structural-break-features]]
- [[fractional-differencing]]
- [[kalman-filter-features]]
- [[spectral-wavelet-features]]
- [[path-signature-features]]
- [[volatility-model-features]]
- [[uncertainty-as-feature]]
- [[regime-features]]
- [[panel-temporal-features]]

## Why It Matters

Financial series thường non-stationary, regime-dependent, noisy, and heteroskedastic. Model-based features compress these temporal properties into interpretable signals downstream models can condition on.

## Sources

- [ch09_README.md](../../raw/articles/chung-khoan/ch09_README.md)
- [[ch09-model-based-features]]
- [[walk-forward-evaluation]]
- [[train-only-preprocessing]]
