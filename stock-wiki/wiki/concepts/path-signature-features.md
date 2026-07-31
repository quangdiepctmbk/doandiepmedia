---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_06_path_signatures.py, ch09_README.md]
---

# Path Signature Features

Path signatures as feature extractors for ordered data (time series) — from rough path theory.

## Definition

Given a d-dimensional path X(t), its signature is the infinite sequence of iterated integrals of X. In practice, depth truncation keeps the first k levels.

| Depth | Terms | Interpretation |
|-------|-------|----------------|
| 1 | d | Net displacement (returns, volume change) |
| 2 | d + d² | Pairwise interactions (lead-lag, area) |
| 3 | d + d³ | Third-order (acceleration, reversal sequences) |

## Time Augmentation

Add time dimension t → path [t, price, volume] để signature captures both value and temporal structure.

## Log-Signature

Truncated log-signature reduces dimension while retaining information — using Baker–Campbell–Hausdorff expansion.

## ESIG Dependency

**Docker required**: `esig` x86-only, runs in `ml4t-py312` Docker image. Không trong default environment.

## When to Use

- **Depth 1** thường đủ cho chuỗi ngắn (≤20 obs)
- **Depth 2** needed for lead-lag detection between multiple series
- **Depth 3+** hiếm khi improve prediction với chi phí dimensionality cao
- **Log-signature** giảm feature count ~50% so với full signature

## Sources

- [ch09_06_path_signatures.py](../../raw/articles/chung-khoan/ch09_06_path_signatures.py)
- [[model-based-feature-extraction]]
- [[spectral-wavelet-features]]
