---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_05_spectral_features.py, ch09_README.md]
---

# Spectral and Wavelet Features

Frequency-domain feature engineering — wavelet decomposition (offline research) và rolling FFT (production).

## Wavelet Families

| Family | Property | Best For |
|--------|----------|----------|
| `db6` (Daubechies) | Good time-frequency localization | General purpose |
| `sym6` (Symlet) | Near-symmetric, less phase distortion | Trend analysis |
| `coif3` (Coiflet) | Near-zero moments | Feature design |

## Scale → Time → Causal Proxy Bridge

| Wavelet Scale | Horizon | Causal Proxy |
|---------------|---------|-------------|
| D1 | 2-4 days | 3-day rolling features |
| D2 | 4-8 days | 5-day rolling features |
| D3 | 8-16 days | 10-day rolling features |
| D4 | 16-32 days | 21-day rolling features |
| D5 | 32-64 days | 63-day rolling features |
| A5 | >64 days | 126-day rolling features |

Quan trọng: wavelet scales là research tool để khám phá dominant cycle lengths → deploy causal proxies thay thế.

## Rolling FFT Production Features

| Feature | Computation | Update |
|---------|-------------|--------|
| `spectral_energy` | Total power (excl. DC) | Daily |
| `dominant_period` | Period of peak frequency | Daily |
| `spectral_entropy` | Normalized spectrum entropy | Daily |
| `low_freq_ratio` | Energy in low frequencies | Daily |
| `energy_period_5` | Power near weekly frequency | Daily |
| `energy_period_21` | Power near monthly frequency | Daily |

## Welch's Method

Robust power spectral density estimation bằng averaged periodograms — uses Welch window with overlaps. Rolling Welch PSD cho time-frequency heatmap.

## Sources

- [ch09_05_spectral_features.py](../../raw/articles/chung-khoan/ch09_05_spectral_features.py)
- [[model-based-feature-extraction]]
- [[feature-design-grammar]]
