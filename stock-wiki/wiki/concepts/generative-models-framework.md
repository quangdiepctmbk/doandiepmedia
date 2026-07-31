---
tags: [concept, generative-models, framework]
---

# Generative Models Framework

Phân loại các mô hình sinh dữ liệu trong tài chính:

## Discriminative vs Generative

| Loại | Mục tiêu | Ví dụ |
|------|----------|-------|
| Discriminative | Học ranh giới quyết định `P(y|x)` | Logistic regression, SVM, neural nets |
| Generative | Học phân phối `P(x)` | VAE, GAN, diffusion, LLM |

## Họ mô hình sinh trong Chương 5

1. **VAE** — Variational Autoencoder: học phân phối tiềm ẩn, ổn định nhưng chất lượng thấp hơn
2. **GANs** ([timegan](./timegan.md), [tailgan](./tailgan-tail-risk.md), [sigcwgan](./sigcwgan.md), [gtgan](./gtgan-irregular.md)) — adversarial training, chất lượng cao, khó huấn luyện
3. **Diffusion models** ([diffusion-models-finance](./diffusion-models-finance.md)) — denoising, ổn định hơn GAN, chất lượng cạnh tranh
4. **LLM-based** ([llm-tabular-generators](./llm-tabular-generators.md)) — serialization + fine-tune cho dữ liệu bảng

## Nguyên tắc chọn

Không có "GAN nào tốt nhất" — chọn **inductive bias** phù hợp với cấu trúc dữ liệu và task:
- Chuỗi thời gian có temporal structure → TimeGAN
- Cần bảo toàn tail risk → Tail-GAN
- Dữ liệu không đều → GT-GAN (Neural ODE)
- Dữ liệu bảng hỗn hợp → GReaT
- Cần privacy guarantee → DP-GAN

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md)
