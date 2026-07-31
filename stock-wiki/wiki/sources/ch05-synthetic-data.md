---
tags: [synthetic-data, chapter-5, source]
title: "Chương 5: Synthetic Financial Data"
author: Stefan Jansen
url: https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/05_synthetic_data
---

# Chương 5: Synthetic Financial Data

Tổng quan về các phương pháp sinh dữ liệu tài chính tổng hợp — từ mô phỏng cổ điển đến GANs, diffusion models, và LLM-based tabular generators.

## Mục lục

| Module | Nội dung | Runtime |
|--------|----------|---------|
| `00_classical_simulation` | Bootstrap, GBM, jump-diffusion, mean reversion, Heston, GARCH | ~ngay |
| `01_timegan` | TimeGAN (Yoon et al., NeurIPS 2019) | ~12p, GPU |
| `02_tailgan_tail_risk` | Tail-GAN — differentiable sorting, VaR/ES | ~6p, GPU |
| `03_sigcwgan_signatures` | Sig-CWGAN — path signatures (Docker x86-only) | ~ |
| `04_gtgan_irregular` | GT-GAN + Neural ODE — irregular timestamps | ~6p, GPU |
| `05_diffusion_ts` | Diffusion-TS (Yuan & Qiao, ICLR 2024) — trend + seasonal decomposition | ~5p, GPU |
| `06_llm_tabular_great` | GReaT — LLM-based tabular data (distilgpt2) | ~13p, GPU |
| `07_dp_gan` | DP-GAN — differential privacy (Opacus) | ~8p, GPU |

## Các chủ đề chính

- [[generative-models-framework]] — discriminative vs generative, VAE/GAN/diffusion/LLM
- [[fidelity-utility-privacy]] — khuôn khổ đánh giá Fidelity-Utility-Privacy
- [[classical-simulation-baselines]] — các baseline có thể giải thích được
- [[financial-stylized-facts]] — các đặc điểm thống kê cần bảo toàn
- [[timegan]] — TimeGAN cho chuỗi thời gian tài chính
- [[tailgan-tail-risk]] — Tail-GAN và bảo toàn rủi ro đuôi
- [[sigcwgan]] — Signature-based CWGAN
- [[gtgan-irregular]] — GT-GAN cho dữ liệu không đều
- [[diffusion-models-finance]] — Diffusion-TS cho chuỗi thời gian
- [[llm-tabular-generators]] — GReaT cho dữ liệu bảng
- [[differential-privacy-generative]] — DP trong sinh dữ liệu

[Source: raw](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md)
