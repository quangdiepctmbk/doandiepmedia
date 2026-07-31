---
type: source
format: jupyter_notebook
raw_path: raw/articles/chung-khoan/factor_regimes.ipynb
ingested: 2026-07-05
url: https://github.com/stefan-jansen/machine-learning-for-trading/blob/main/01_process_is_edge/factor_regimes.ipynb
---

# Factor-Based Regime Detection with GMM

Notebook chương 1 ML4T: phát hiện chế độ thị trường dùng GMM trên AQR Century of Factor Premia.

## Tổng quan

Dùng Gaussian Mixture Models (GMM) để phát hiện regime trên factor returns (Value, Momentum, Carry, Defensive) xuyên 1927-2024.

## Kết quả chính

- **BIC chọn K=2**: Risk-On / Risk-Off. Silhouette cao nhất ở K=2 (0.27).
- **Risk-Off**: Vol gấp 2.2 lần, Sharpe 0.12 (vs 1.11), max DD -77%.
- **Value nghịch chu kỳ**: +5.3% trong Risk-Off vs +1.6% trong Risk-On.
- **Momentum thuận chu kỳ**: +4.5% Risk-On vs +0.4% Risk-Off.
- **Carry và Defensive** âm trong Risk-Off (-0.6%, -0.5%).
- **Bonds vượt trội** trong Risk-Off (+4.2% vs +0.8%).
- Trung bình chuyển regime mỗi ~4 tháng → phù hợp để hiểu thị trường hơn là tactical allocation.

## Cảnh báo

Phân tích này là **ex-post** (dùng full history để fit). Không dùng làm feature dự báo mà không có walk-forward validation (xem Chương 6+).

## Liên kết

- [[market-regimes]]
- [[process-is-edge]]
- [[machine-learning-for-trading]]
