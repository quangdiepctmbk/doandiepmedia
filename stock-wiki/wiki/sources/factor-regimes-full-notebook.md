---
type: source
format: notebook_full
raw_path: raw/articles/chung-khoan/factor-regimes-notebook-full.md
ingested: 2026-07-05
---

# Factor Regimes Notebook — Full Content (Code + Output)

Bản đầy đủ Jupyter notebook `factor_regimes.ipynb` — gồm cả markdown, code Python và output. Raw file tại `raw/articles/chung-khoan/factor-regimes-notebook-full.md` (39.8KB).

## Cấu trúc code

### Setup & Helpers
- Imports: pandas, numpy, sklearn.mixture.GaussianMixture, sklearn.metrics.silhouette_score
- Grid search GMM (2-6 clusters) với BIC, AIC, silhouette
- Hàm helper: `fit_gmm_grid()`, `plot_cluster_grid()`, `assign_regimes()`

### Load Data (Code Cell)
- Đọc AQR Century of Factor Premia parquet: Value, Momentum, Carry, Defensive cross-asset
- Chọn 4 factor core: All asset classes Value/Momentum/Carry/Defensive + Equity indices Market

### Fit GMM (Code Cell)
```python
gmm = GaussianMixture(n_components=2, random_state=42, n_init=10)
gmm.fit(scaler.transform(factors))
labels = gmm.predict(scaler.transform(factors))
```
- K=2: BIC thấp nhất (26170), silhouette cao nhất (0.27)
- K>=4 cho silhouette âm (chồng lấn)

### Visualize (Code Cell)
- Regime timeline 1927-2024 với Risk-On/Off bands
- Volatility by regime: Risk-Off vol 2.2x
- Factor behavior: Value countercyclical (+5.3%), Momentum procyclical (+4.5%)
- Regime statistics table: Risk-On Sharpe 1.11, Risk-Off 0.12
- Duration analysis: ~4 month average per regime, Risk-Off avg 2 tháng

### Persist (Code Cell)
- Lưu GMM params + labels cho book figure generation

## Liên kết

- [[factor-regimes]]
- [[process-is-edge]]
- [[machine-learning-for-trading]]
