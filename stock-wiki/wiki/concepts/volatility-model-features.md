---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_07_arima_features.py, ch09_08_garch_volatility.py, ch09_09_har_rough_volatility.py, ch09_README.md]
---

# Volatility Model Features

Volatility là phần forecastable nhất của financial time series — fitted volatility models convert predictability vào usable features.

## ARIMA Features (ch09_07)

ARIMA used as **feature extractor**, not standalone forecaster. Key outputs:

- **Residuals**: serial-correlation-free signal (what ARIMA can't predict)
- **Forecasts**: n-step ahead point prediction
- **Forecast uncertainty**: prediction interval width

Finding: Simple ARIMA mean models extract **limited signal** từ daily returns (near-random walk). AR(1) beats ARIMA(p,d,q) on directional metrics.

## GARCH Features (ch09_08)

| Feature | Description |
|---------|-------------|
| `conditional_volatility` | σ̂ₜ — fitted conditional standard deviation |
| `persistence` | α + β (GARCH stationarity constraint < 1) |
| `leverage_effect` | EGARCH — negative returns → higher vol (Nelson) |

**ARCH-LM test**: confirms volatility clustering before fitting.

**Stationarity constraint**: α + β < 1 for GARCH(1,1); if α+β ≈ 1 → IGARCH (integrated variance).

## EGARCH

Captures **leverage effect**: negative returns có impact lớn hơn positive returns lên future volatility. Dùng cho risk management và VaR estimation.

## HAR Model (ch09_09)

Heterogeneous Autoregressive model for realized volatility — three components:

- **Daily** (RV_daily): short-term noise
- **Weekly** (RV_weekly): medium-term (5-day avg)
- **Monthly** (RV_monthly): long-term (22-day avg)

HAR coefficients reveal **volatility term structure** — `vol_term_structure = RV_daily / RV_monthly` là regime indicator (high ratio = turbulent market).

## Hurst Exponent & Rough Volatility

R/S analysis và DFA (Detrended Fluctuation Analysis) for Hurst exponent:

- **H ≈ 0.5**: random walk
- **H > 0.5**: trending / persistent
- **H < 0.5**: mean-reverting
- **H ≈ 0.1**: **rough volatility** — stylized fact of financial volatility (Gatheral et al. 2014)

## Feature Catalog

| Feature | Source | Update |
|---------|--------|--------|
| `rv_daily` | Garman-Klass range | Daily |
| `rv_weekly` / `rv_monthly` | Multi-horizon avg | Daily |
| `daily_contribution` / `monthly_contribution` | HAR β coefficients | Weekly/monthly |
| `vol_term_structure` | RV ratios | Daily |
| `hurst_exponent` | DFA on returns (252d) | Weekly |
| `roughness_h` | DFA on log-vol (252d) | Weekly |

## Sources

- [ch09_07_arima_features.py](../../raw/articles/chung-khoan/ch09_07_arima_features.py)
- [ch09_08_garch_volatility.py](../../raw/articles/chung-khoan/ch09_08_garch_volatility.py)
- [ch09_09_har_rough_volatility.py](../../raw/articles/chung-khoan/ch09_09_har_rough_volatility.py)
- [[model-based-feature-extraction]]
- [[stationarity-diagnostic-features]]
- [[uncertainty-as-feature]]
