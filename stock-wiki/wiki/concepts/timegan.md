---
tags: [concept, synthetic-data, gan, time-series]
---

# TimeGAN

TimeGAN (Yoon, Jarrett & van der Schaar, NeurIPS 2019) — kiến trúc nền tảng cho sinh chuỗi thời gian tài chính tổng hợp.

## Cơ chế

Kết hợp adversarial loss (GAN) + supervised loss (autoregressive) để học temporal dynamics:
- **Embedding network** — ánh xạ chuỗi gốc sang latent space
- **Generator** — sinh latent embeddings
- **Recovery network** — ánh xạ latent về chuỗi gốc
- **Discriminator** — phân biệt thật/giả

## So sánh với vanilla GAN

| Khía cạnh | Vanilla GAN | TimeGAN |
|-----------|-------------|---------|
| Temporal structure | Không xử lý | Joint distribution qua autoregressive |
| Ổn định huấn luyện | Không | Tốt hơn nhờ supervised loss |
| Dữ liệu | IID | Time series |
| Khởi tạo | Random noise | Embedding từ chuỗi thật |

## Data sử dụng
`multi_stock_data`, `state_dict`, `us_equities`

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]], [[fidelity-utility-privacy]]
