---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_03_fractional_differencing.py, ch09_README.md]
---

# Fractional Differencing (FFD)

Fractional differentiation — achieving stationarity while preserving maximum memory, unlike integer differencing which destroys all long-term dependencies.

## Definition

FFD applies binomial expansion weights with fractional exponent d ∈ (0, 1):

- d=0: original series (full memory, non-stationary)
- d=1: first difference (stationary, zero memory)
- d=0.4–0.5: sweet spot — stationarity + memory preservation

## Asset Class d Recommendations

| Asset Class | d | Rationale |
|-------------|---|-----------|
| US Equities | 0.4 | Moderate persistence |
| Fixed Income | 0.5 | High persistence |
| Crypto | 0.5–0.6 | Strong trending |
| Commodities | 0.4 | Similar to equities |
| FX | 0.3–0.4 | Mean-reverting tendency |

## Key Mechanics

- **FFD weights**: binomial expansion coefficients, computed with `ffd_weights()` from ml4t-engineer
- **Validity mask**: NaN-padded initial segment (sample loss = `threshold_weight` window)
- **Weight drop threshold**: default 1e-5 — cắt weights dưới ngưỡng để kiểm soát sample loss
- **Boundary convention**: sample loss tính từ observation đầu series, FFD output tự động align index

## ml4t-engineer Interface

- `ffd()` — single-column FFD
- `detect_fractional_order()` — auto select d to achieve stationarity
- `select_asset_d()` — map asset class → recommended d (bounded grid, avoid lookahead)

## Why It Matters

Đây là feature engineering step đầu tiên cho time-series models: FFD features preserve enough memory để models học được long-term patterns, nhưng series đủ stationary để statistical inference valid.

## Sources

- [ch09_03_fractional_differencing.py](../../raw/articles/chung-khoan/ch09_03_fractional_differencing.py)
- [[model-based-feature-extraction]]
- [[stationarity-diagnostic-features]]
- [[price-volume-features]]
