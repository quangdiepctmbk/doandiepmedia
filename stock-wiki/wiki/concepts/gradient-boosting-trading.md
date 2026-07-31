---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_README.md]
---

# Gradient Boosting for Trading

Gradient Boosting Machines (GBMs) là family của tree ensemble methods built on sequential error correction — mỗi cây mới fit vào residual của cây trước. Đây là state-of-the-art cho tabular financial data.

## Why GBMs Work for Financial Data

- Handle nonlinear, threshold-driven structure (linear models miss)
- Naturally handle missing values, mixed data types
- Robust to irrelevant features (feature selection happens at split level)
- Good with small-to-moderate datasets (unlike deep learning)

## Libraries (Ch12)

- **XGBoost**: strong regularization, mature ecosystem, GPU support
- **LightGBM**: fastest training, GOSS/EFB, leaf-wise growth
- **CatBoost**: native categorical handling, unbiased gradient estimates

## Links

- [[ensemble-foundations-finance]]
- [[gbm-library-benchmark]]
- [[dl-vs-gbm-tabular]]
- [[treeshap-interpretability]]
- [[regularized-regression-trading]]
- [[ml-pipeline-trading]]

## Sources

- [ch12_README.md](../../raw/articles/chung-khoan/ch12_README.md)
- [[ch12-gradient-boosting]]
