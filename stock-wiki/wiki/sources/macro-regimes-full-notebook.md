---
type: source
format: notebook_full
raw_path: raw/articles/chung-khoan/macro-regimes-notebook-full.md
ingested: 2026-07-05
url: https://github.com/stefan-jansen/machine-learning-for-trading/blob/main/01_process_is_edge/macro_regimes.ipynb
---

# Macro-Based Regime Detection — Full Notebook

Notebook chương 1 ML4T: dùng macro indicators từ FRED để phát hiện regime, rồi validation bằng S&P 500 volatility và drawdown.

## Mục tiêu

- Cluster monthly macro indicators bằng GMM, K-Means, hierarchical clustering
- Validate clusters với realized volatility và drawdown của S&P 500
- So sánh core 4 indicators và extended FRED panel
- Dùng PCA để lọc nhiễu trước clustering

## Core indicators

- `UNRATE` — thất nghiệp
- `DFF` — Fed Funds rate
- `T10Y2Y` — yield curve spread 10Y-2Y
- `CPIAUCSL` → CPI YoY

## Core model kết quả

- Monthly data: 289 months (2002-2026)
- GMM 4 regimes silhouette: 0.252
- Regime labels:
  - Cluster 0: Expansion
  - Cluster 1: Crisis
  - Cluster 2: Recovery
  - Cluster 3: Tightening

## S&P 500 validation

| Regime | Months | Annual Vol | Max Drawdown |
|---|---:|---:|---:|
| Expansion | 77 | 12.0% | 14.6% |
| Tightening | 98 | 15.0% | 42.2% |
| Recovery | 98 | 15.2% | 52.6% |
| Crisis | 4 | 16.0% | 9.9% |

## Extended indicators

25 FRED series: rates, yield curve, VIX, initial claims, CPI/core CPI/PCE, unemployment, payrolls, participation, industrial production, M2, GDP.

- GMM silhouette: 0.417
- K-Means silhouette: 0.448
- PCA: PC1+PC2 explain 80.4%, PC1-PC4 explain 93.6%
- GMM on PCA silhouette: 0.396

## Key insight

Macro regimes line up với volatility environments rõ hơn average returns. Vì vậy dùng macro regime cho **risk management**: exposure caps, hedging triggers, de-risking rules — không dùng như return forecast.

## Liên kết

- [[market-regimes]]
- [[factor-regimes]]
- [[two-sigma-regime-modeling]]
