---
type: concept
domain: trading
created: 2026-07-05
updated: 2026-07-05
sources: [process-is-edge]
---

# Market Regimes

Tư duy về chế độ thị trường (regime) — sử dụng Gaussian Mixture Models (GMM) để phát hiện trạng thái thị trường.

## Định nghĩa

Thị trường không đứng yên. Nó chuyển đổi giữa các chế độ (bull, bear, sideways, high-vol, low-vol). Nhận diện regime giúp quản lý rủi ro thích ứng.

## Nguyên tắc

- Regime là **risk lens** (kính lọc rủi ro), không phải là timing signal
- Mô hình tĩnh suy giảm khi thị trường chuyển regime
- Cần phân biệt: structural breaks, data drift, concept drift

## Công cụ

- `factor_regimes.ipynb`: GMM trên factor returns từ AQR Century of Factor Premia
- `macro_regimes.ipynb`: Chỉ báo vĩ mô FRED, kiểm định với S&P 500 volatility và drawdowns

## Liên kết

- [[ml4t-workflow]]
- [[evidence-boundary]]
- [[machine-learning-for-trading]]
