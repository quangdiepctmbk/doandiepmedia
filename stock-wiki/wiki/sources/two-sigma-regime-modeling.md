---
type: source
format: article
raw_path: raw/articles/chung-khoan/two-sigma-regime-modeling.md
ingested: 2026-07-05
url: https://www.twosigma.com/articles/a-machine-learning-approach-to-regime-modeling/
---

# Two Sigma: A Machine Learning Approach to Regime Modeling

Bài báo kỹ thuật của Alex Botte & Doris Bao (10/2021). Dùng GMM trên 17 factors của Two Sigma Factor Lens.

## Tổng quan

- **Approach:** Data-driven regime detection bằng GMM (unsupervised learning)
- **Input:** 17 factors từ Two Sigma Factor Lens (data từ 1970s)
- **Output:** 4 market conditions / clusters
- **Ưu điểm:** Không cần định nghĩa regime thủ công, model là data-driven
- **Nhược điểm:** Khó gán trực giác kinh tế cho từng regime

## 4 Market Conditions

### 1. Crisis
- Global Equity và Credit negative mean returns (duy nhất trong 4 MC)
- Emerging Markets yếu hơn Developed Markets
- U.S. Local Equity outperforms global (flight to quality)
- Equity Short Volatility negative (vol cao)
- Interest Rates positive (trái phiếu chính phủ — flight to safety)
- Local Inflation negative (lạm phát không giúp ích)
- Value, Quality, Low Risk positive; Small Cap negative
- Trend Following large positive return
- Factor correlations tăng cao nhất (dù vẫn gần zero)
- **Vol cao nhất** trong 4 MC
- **Xảy ra:** 1987 crash, GFC 2008, COVID 2020, European Sovereign Debt 2010s, Taper Tantrum 2013
- Tần suất: ~15-20% thời gian 1971-2020

### 2. Steady State
- Equity, Credit, style factors đều positive
- Local Equity và EM gần như bằng nhau
- Local Inflation nhẹ dương
- **Xảy ra:** Phổ biến nhất (1971-2020), đặc biệt thống trị thập kỷ sau 2010 nhờ central bank

### 3. Inflation
- Local Inflation double-digit mean return (cao nhất 4 MC)
- Equity và Interest Rates positive nhẹ (underperform)
- Foreign Currency cao nhất (USD yếu so với G10)
- **Xảy ra:** Chỉ trong 1970s-1980s, không xuất hiện sau 2010

### 4. Walking on Ice (WOI)
- Equity positive nhưng vol cao (cao thứ 2 sau Crisis)
- Factor volatilities cao hơn trung bình 1.6pp
- Momentum ngoại lệ (underperform)
- Value vol 18.2% (vs 8.9% LT), Momentum 19.1% (vs 10.5%)
- **Xảy ra:** Tech bubble 1990s-2000s, post-GFC và post-COVID recovery, 2021 WOI tăng trở lại
- Diễn giải: risk-on bubble forming / fragility

## Timeline lịch sử

- **1970s-1980s:** Inflation chiếm ưu thế
- **Late 1990s-2000s:** WOI (tech bubble), rải rác Crisis
- **1987:** Crisis (stock market crash)
- **2008:** Crisis (GFC)
- **2000s-2010s:** Steady State thống trị, rải rác Crisis ngắn (European Debt, Taper Tantrum)
- **2020:** Crisis (COVID), sau đó WOI → Steady State
- **2021:** Chuyển dần về WOI (fragility), Inflation probability = 0

## So sánh với factor_regimes.ipynb (ML4T)

| Thuộc tính | Two Sigma | ML4T factor_regimes |
|---|---|---|
| Dataset | Two Sigma Factor Lens (17 factors) | AQR Century of Factor Premia (4-5 factors) |
| Clusters | 4 (K=4) | 2 (K=2, BIC/silhouette) |
| Method | GMM | GMM |
| Thời gian | 1970s-2021 | 1927-2024 |

## Liên kết

- [[market-regimes]]
- [[factor-regimes]]
- [[machine-learning-for-trading]]
