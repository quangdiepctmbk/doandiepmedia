---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_01_ensemble_foundations.py]
---

# Ensemble Foundations: RF → GBM

Random Forests và Gradient Boosting Machines đều là tree ensembles, nhưng khác biệt cốt lõi:

- **Bagging (RF)**: parallel trees, each on bootstrap sample. Reduces variance, không giảm bias.
- **Boosting (GBM)**: sequential trees, mỗi cây fit residual của cây trước. Reduces bias.

NB01 benchmarks RF vs XGBoost/LightGBM/CatBoost trên Chen-Pelger-Zhu firm characteristics panel: GBMs outperform RF consistently.

## Links

- [[gradient-boosting-trading]]
- [[gbm-library-benchmark]]
- [[regularized-regression-trading]]
- [[ml-pipeline-trading]]

## Sources

- [ch12_01_ensemble_foundations.py](../../raw/articles/chung-khoan/ch12_01_ensemble_foundations.py)
