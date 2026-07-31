---
tags: [concept, synthetic-data, evaluation]
---

# Fidelity-Utility-Privacy Framework

Khuôn khổ đánh giá dữ liệu tổng hợp trong tài chính, chia làm 3 trụ cột:

## 1. Fidelity (Tính trung thực)

Dữ liệu tổng hợp có giữ được các [[financial-stylized-facts]] không?
- Phân phối lợi suất (heavy tails, skewness)
- Tự tương quan và volatility clustering
- Cross-sectional correlations
- Tail risk (VaR, Expected Shortfall)

## 2. Utility (Tính hữu dụng)

Mô hình huấn luyện trên dữ liệu tổng hợp có hiệu quả trên dữ liệu thật không?
- **TSTR** (Train Synthetic, Test Real) — phương pháp đánh giá chính
- So sánh Sharpe ratio, drawdown, turnover giữa synthetic-trained và real-trained

## 3. Privacy (Tính riêng tư)

Dữ liệu tổng hợp có làm lộ thông tin gốc không?
- **Membership inference attacks** — kiểm tra xem có thể suy ra bản ghi gốc không
- **Differential privacy** ([[differential-privacy-generative]]) — giới hạn formal leakage
- **Overfitting to generator** — mô hình học sai pattern do generator tạo artifact

## Raw source
[ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md)
