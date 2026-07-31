---
tags: [concept, synthetic-data, privacy, dp]
---

# Differential Privacy in Generative Models

DP-GAN — huấn luyện GAN với đảm bảo privacy chính thức bằng **Opacus** (PyTorch DP library).

## Cơ chế

- **Gradient clipping**: giới hạn ảnh hưởng của từng mẫu lên gradient
- **Noise addition**: thêm Gaussian noise vào gradient
- **Privacy budget (ε, δ)**: đo lường formal leakage

## Tác động

| Khía cạnh | Không DP | Có DP |
|-----------|----------|-------|
| Bảo vệ membership | Không | Formal guarantee |
| Chất lượng ảnh | Cao | Thấp hơn (noise trade-off) |
| Tail risk bảo toàn | Tốt | Suy giảm |
| Số epoch huấn luyện | Nhiều | Bị giới hạn bởi budget |

## Trade-off: Privacy vs Utility

- Budget càng nhỏ (ε càng thấp), bảo vệ càng mạnh nhưng chất lượng giảm
- Cần cân bằng: vừa đủ privacy để chống membership inference, vừa đủ utility để TSTR có ý nghĩa

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[fidelity-utility-privacy]], [[generative-models-framework]]
