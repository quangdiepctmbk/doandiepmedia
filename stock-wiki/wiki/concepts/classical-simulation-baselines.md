---
tags: [concept, synthetic-data, baseline]
---

# Classical Simulation Baselines

Các mô phỏng cổ điển dùng làm baseline cho sinh dữ liệu tài chính — dễ hiểu, mẫu hiệu quả, dễ kiểm chứng.

## Các mô hình

1. **Bootstrap** — lấy mẫu có hoàn lại từ chuỗi lợi suất thực; bảo toàn phân phối nhưng mất temporal structure
2. **Geometric Brownian Motion (GBM)** — giả định log-return phân phối chuẩn, phù hợp cho baseline đơn giản
3. **Jump-Diffusion** — GBM + Poisson jumps (Merton model); capture được fat tails một phần
4. **Mean Reversion** — Ornstein-Uhlenbeck process; phù hợp cho cặp tiền tệ, lãi suất
5. **Heston Model** — stochastic volatility; volatility clustering, leverage effect
6. **GARCH** — autoregressive conditional heteroskedasticity; chuẩn mực cho volatility modeling

## Tại sao vẫn quan trọng?

- **Interpretable** — mỗi tham số có ý nghĩa tài chính rõ ràng
- **Sample-efficient** — chỉ cần vài tham số
- **Baseline** — mọi learned generator phải đánh bại trên diagnostics thực sự quan trọng

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | Xem thêm: [[generative-models-framework]], [[financial-stylized-facts]]
