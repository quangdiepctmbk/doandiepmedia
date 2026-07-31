---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_02_structural_breaks.py, ch09_README.md]
---

# Structural Break Features

Phát hiện và encode structural breaks làm features cho downstream models.

## Classical Methods

- **Zivot-Andrews**: unit root test với 1 endogenous break — phát hiện break point duy nhất
- **Bai-Perron** (via `ruptures`): multiple break points — PELT (automatic) và Binary Segmentation (fixed N)
- **CUSUM**: cumulative sum — detects **sustained drift**, one-sided, statistic stays elevated permanently
- **MOSUM**: moving sum (fixed-width window) — detects **abrupt localized shifts**, peaks at break then decays. Bandwidth h controls sensitivity.

## Feature Families

### Location Shift
Test pre/post mean difference (t-test, Mann-Whitney, diff of medians)

### Scale Shift
Compare pre/post variance, IQR, coefficient of variation — robust to level changes

### Distribution Shift
Wasserstein distance, KL divergence, Jensen-Shannon — full distribution comparison

### Dependence Shift
Autocorrelation change test — AR(1) coefficient comparison, Ljung-Box

### Fisher Aggregation
Combine p-values từ multiple tests và window sizes để có break signal tổng hợp

## ADIA Lab Approach

Break detection reframed as **binary classification** — 58 statistical features pre/post boundary + LightGBM classifier.

## Break-Derived Features

- `za_break_detected` — binary
- `days_since_break` — recency
- `pre_break_mean` / `post_break_mean` — level changes
- PELT/BinSeg break indices — timestamps

## Sources

- [ch09_02_structural_breaks.py](../../raw/articles/chung-khoan/ch09_02_structural_breaks.py)
- [[model-based-feature-extraction]]
- [[stationarity-diagnostic-features]]
