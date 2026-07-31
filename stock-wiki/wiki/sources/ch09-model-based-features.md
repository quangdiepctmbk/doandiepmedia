---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch09_README.md
ingested: 2026-07-25
related_raw:
  - ch09_01_visual_diagnostics.py
  - ch09_02_structural_breaks.py
  - ch09_03_fractional_differencing.py
  - ch09_04_kalman_filter.py
  - ch09_05_spectral_features.py
  - ch09_06_path_signatures.py
  - ch09_07_arima_features.py
  - ch09_08_garch_volatility.py
  - ch09_09_har_rough_volatility.py
  - ch09_10_uncertainty_features.py
  - ch09_11_hmm_regimes.py
  - ch09_12_wasserstein_regimes.py
  - ch09_13_regime_as_feature.py
  - ch09_14_panel_features.py
  - ch09_case_study_temporal_summary.py
---

# Model-Based Features — Chương 9 (ML4T)

## Summary

Chương này reframe diagnostic testing và time-series modeling thành một **feature engineering pipeline**: thay vì dùng stationarity test, break detection, GARCH làm bước kiểm tra tiền xử lý, tất cả đều trở thành feature generators cho ML models downstream.

14 notebooks chia làm 6 sections:
1. **9.1 Diagnostics & Stationarity** — Visual diagnostics, ADF/KPSS, fractional differencing (FFD), rolling stationarity features
2. **9.2 Signal Transforms** — Kalman filter (level/slope/innovation), spectral/wavelet features, path signatures
3. **9.3 Volatility Features** — ARIMA residuals, GARCH/EGARCH conditional vol, HAR model, Hurst exponent, rough volatility
4. **9.4 Uncertainty Features** — Bayesian posterior widths, ARIMA forecast uncertainty (conformal prediction)
5. **9.5 Regime Features** — HMM, Markov-switching AR, Wasserstein regime clustering, soft regime-as-feature
6. **9.6 Cross-Sectional & Panel Features** — Cointegration, Kalman hedge ratios, O-U half-life, cross-sectional ranking

Plus case study thu thập temporal features từ tất cả case studies khác.

## Key Takeaways

- **Stationarity không phải binary property** — rolling ADF/KPSS là time-varying features, fractional differencing (d=0.4 US equities) preserves memory while achieving stationarity
- **CUSUM vs MOSUM**: CUSUM tích lũy drift (phát hiện sustained shifts), MOSUM cục bộ (phát hiện abrupt shifts)
- **Kalman filter tạo 4 features**: level, trend, innovation (surprise), uncertainty (state variance)
- **Wavelets**: D1–D5 scales tương ứng 3–63 day rolling proxies — bridge để dùng wavelets làm causal features
- **GARCH**: conditional volatility α+β<1 là stationarity constraint; EGARCH captures leverage effect (negative returns → higher vol)
- **HAR model**: realized volatility decomposition dựa trên daily/weekly/monthly components; rough volatility (H≈0.1) là stylized fact
- **Regime as feature** tốt hơn regime switching — dùng regime probabilities làm soft conditioning features thay vì hard switch giữa các models
- **Wasserstein regime clustering**: dùng optimal transport thay vì moment features (Horvath et al. 2021)
- **Panel features**: cross-sectional ranking, relative-to-sector/market, cointegration screening, O-U half-life

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 9
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/09_model_based_features)
- [[ch08-financial-features]] (previous chapter)
