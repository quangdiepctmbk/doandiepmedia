---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_01_visual_diagnostics.py, ch09_README.md]
---

# Stationarity Diagnostic Features

Diagnostic features từ visual inspection và stationarity tests — dùng làm time-varying inputs thay vì một-time preprocessing gate.

**Key components**: ADF + KPSS joint decision matrix, Ljung-Box trên squared returns (ARCH detection), rolling stationarity regime.

## ADF + KPSS Decision Matrix

| ADF | KPSS | Conclusion |
|-----|------|------------|
| Reject H0 | Fail to reject H0 | **Stationary** |
| Fail to reject H0 | Reject H0 | **Non-stationary** |
| Reject H0 | Reject H0 | Trend-stationary |
| Fail to reject H0 | Fail to reject H0 | Inconclusive |

ml4t-diagnostic còn thêm Phillips-Perron → three-test consensus với agreement score.

## Rolling Feature Catalog

| Feature | Computation | Update |
|---------|-------------|--------|
| `adf_statistic` | Rolling 252-day ADF | Weekly |
| `kpss_statistic` | Rolling 252-day KPSS | Weekly |
| `stationarity_regime` | Joint decision matrix | Weekly |

## ARCH Effects

Ljung-Box trên squared returns phát hiện volatility clustering — prerequisite cho GARCH (NB08).

## Sources

- [ch09_01_visual_diagnostics.py](../../raw/articles/chung-khoan/ch09_01_visual_diagnostics.py)
- [[model-based-feature-extraction]]
- [[fractional-differencing]]
