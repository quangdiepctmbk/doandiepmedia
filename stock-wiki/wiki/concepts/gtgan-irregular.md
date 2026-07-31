---
tags: [concept, synthetic-data, gan, neural-ode]
---

# GT-GAN (Irregular Time Series)

GT-GAN-inspired model (Jeon et al., NeurIPS 2022) — dùng **Neural ODEs** để xử lý chuỗi thời gian tài chính có timestamps không đều.

## Vấn đề

Dữ liệu tài chính thực thường có khoảng thời gian không đều (transaction-level, dollar bars). GANs tiêu chuẩn yêu cầu grid đều.

## Giải pháp

- **Neural ODE** — mô hình hóa dynamics liên tục thay vì rời rạc
- Cho phép sinh dữ liệu tại bất kỳ timestamp nào
- Kết hợp adversarial loss với ODE solver

## Data sử dụng
NVDA dollar bars từ Databento (Chapter 3 bar sampling)

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]]
