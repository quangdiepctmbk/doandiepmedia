---
tags: [concept, synthetic-data, gan, path-signatures]
---

# Sig-CWGAN (Signature-based Conditional Wasserstein GAN)

Sử dụng **path signatures** (rough paths theory) để capture path-level fidelity của chuỗi thời gian tài chính.

## Cơ chế

- **Path signatures** — biểu diễn toàn bộ đường đi (path) thành một tập đặc trưng có cấu trúc đại số
- **Conditional Wasserstein GAN** — generator có điều kiện với Wasserstein distance
- Sig-CWGAN kết hợp: signature features làm inductive bias + Wasserstein loss cho ổn định

## Yêu cầu

- **Docker x86-only**: cần `signatory` và `esig` packages
- Chạy với profile `py312`

## Data sử dụng
`sp500_log_returns`, `state_dict`

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]]
