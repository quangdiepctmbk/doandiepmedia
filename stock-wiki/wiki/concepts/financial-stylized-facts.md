---
tags: [concept, synthetic-data, stylized-facts]
---

# Financial Stylized Facts

Các đặc điểm thống kê phổ quát của chuỗi lợi suất tài chính mà mọi generator phải bảo toàn:

1. **Heavy tails** — phân phối lợi suất có đuôi dày hơn normal distribution
2. **Volatility clustering** — biến động mạnh đi cùng nhau
3. **Leverage effect** — volatility tăng khi giá giảm
4. **Absence of autocorrelation** — lợi suất gần như không tự tương quan nhưng lợi suất bình phương thì có
5. **Skewness** — phân phối lệch (thường lệch trái)
6. **Gain/loss asymmetry** — drawdown khác với upswing
7. **Aggregational Gaussianity** — phân phối lợi suất tiến tới chuẩn khi tăng tần số

## Ứng dụng

Dùng để diagnostics trực quan khi so sánh dữ liệu thật vs tổng hợp, kết hợp với [[fidelity-utility-privacy]].

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md)
