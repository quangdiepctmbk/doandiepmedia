---
tags: [concept, synthetic-data, gan, tail-risk]
---

# Tail-GAN

Tail-GAN (Cont, Xu & Zhang, 2022) — GAN sử dụng **differentiable sorting** để bảo toàn đặc điểm rủi ro đuôi (VaR, Expected Shortfall) trong kịch bản tài chính tổng hợp.

## Vấn đề

GANs tiêu chuẩn không bảo toàn tail risk — phân phối tổng hợp thường có đuôi nhẹ hơn thực tế.

## Giải pháp

- **Differentiable sorting operators** — cho phép gradient flow qua thống kê thứ tự (order statistics)
- Loss function bao gồm tail risk metrics (VaR, ES) trong quá trình huấn luyện

## Data sử dụng
`etf_returns`, `etfs`, `state_dict`

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]], [[financial-stylized-facts]]
