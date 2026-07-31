---
tags: [concept, synthetic-data, diffusion, time-series]
---

# Diffusion Models for Financial Time Series

**Diffusion-TS** (Yuan & Qiao, ICLR 2024) — diffusion model thiết kế riêng cho chuỗi thời gian tài chính.

## Cơ chế

- **Forward process**: thêm noise vào dữ liệu gốc dần dần
- **Reverse process**: khử noise (denoising) để khôi phục dữ liệu
- **Conditional guidance**: hỗ trợ stress testing theo regime

## Điểm khác biệt so với diffusion thuần

Diffusion-TS phân tách prediction đầu ra thành 2 thành phần:
- **Trend component** — polynomial regression (slow drift)
- **Seasonal component** — Fourier basis (periodic patterns)

Tương tự **STL decomposition** (Seasonal-Trend decomposition) nhưng học end-to-end trong diffusion framework.

## Ưu điểm

- Ổn định hơn adversarial training (GAN)
- Chất lượng cạnh tranh
- Hỗ trợ conditional generation theo regime

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]], [[fidelity-utility-privacy]]
