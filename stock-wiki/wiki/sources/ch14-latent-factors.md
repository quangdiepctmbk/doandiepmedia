---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch14_README.md
ingested: 2026-07-26
related_raw:
  - ch14_01_pca_equity_sectors.py
  - ch14_02_eigenportfolios.py
  - ch14_03_yield_curve_decomposition.py
  - ch14_04_ipca.py
  - ch14_05_rp_pca.py
  - ch14_06_conditional_autoencoder.py
  - ch14_07_stochastic_discount_factor.py
  - ch14_08_supervised_autoencoder.py
  - ch14_09_case_study_insights.py
---

# Latent Factor Models — Chương 14 (ML4T)

## Summary

Chương 14 reframe **factor zoo** (hàng trăm named factors) thành bài toán học lower-dimensional risk structure trực tiếp từ dữ liệu. Từ PCA kinh điển đến deep learning autoencoders và stochastic discount factor models, với insight quan trọng: phân biệt **attribution factors** (explain covariance) vs **priced factors** (explain expected returns).

9 notebooks chia làm 8 sections:

1. **14.1 Making the Case** — Factor zoo → latent factors, covariance vs pricing distinction
2. **14.2 PCA Foundation** — Eigenvalues, loading stability, bootstrap diagnostics
3. **14.3 Eigenportfolios** — PCA eigenvectors → portfolio weights, stat-arb, HPCA
4. **14.4 Yield Curve** — Level / Slope / Curvature = textbook latent factor success
5. **14.5 Advanced Models** — IPCA (Kelly-Pruitt-Su 2019), RP-PCA (Lettau-Pelger 2020)
6. **14.6 Conditional Autoencoder** — Gu-Kelly-Xiu 2019: nonlinear latent factors
7. **14.7 Supervised Autoencoder & SDF** — Adversarial SDF + Jane Street Kaggle SAE
8. **14.8 Case Studies** — Marchenko-Pastur diagnostic: most datasets lack cross-sectional breadth for latent factors

## Key Takeaways

- **PCA works where structure is low-rank**: yield curve (3 factors), sector ETFs (market + rotation)
- **Loading stability is a real issue** — bootstrap to diagnose
- **Eigenportfolios**: top PCs → long-short portfolios, stat-arb signals
- **IPCA**: instrumented PCA — firm characteristics determine time-varying betas
- **RP-PCA**: risk-premium PCA — objective = pricing error, not variance
- **CAE** (Gu-Kelly-Xiu 2019): autoencoder with firm characteristics → nonlinear latent factors. Walk-forward + ensemble + SHAP
- **Adversarial SDF** (Chen-Pelger-Zhu 2021): no-arbitrage GMM objective
- **Supervised Autoencoder**: reconstruction + auxiliary + main prediction loss (Jane Street Kaggle)
- **Marchenko-Pastur test**: hầu hết case studies không đủ breadth cho latent factor extraction

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 14
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/14_latent_factors)
- [[ch13-dl-time-series]] (previous chapter)
