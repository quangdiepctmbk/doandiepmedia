---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_02_gbm_comparison.py]
---

# GBM Library Benchmark

So sánh 4 libraries GBM (sklearn HistGradientBoosting → XGBoost → LightGBM → CatBoost) trên ETF panel, bao gồm:

- **Regression**: 21-day forward returns, walk-forward CV
- **Learning-to-rank**: dùng `Objective.LAMBDAMART` của LightGBM (ListNet / LambdaRank)
- **Monotonic constraints**: `monotone_constraints=(1,)` — features có tín hiệu one-directional
- **Scale benchmark**: 5M rows
- **CPU vs GPU** comparison

**Kết quả chính**: Spread giữa 3 libraries nhỏ — chọn theo categorical structure, compute, latency, deployment.

## Links

- [[gradient-boosting-trading]]
- [[ensemble-foundations-finance]]
- [[optuna-hyperparameter-tuning]]
- [[walk-forward-evaluation]]

## Sources

- [ch12_02_gbm_comparison.py](../../raw/articles/chung-khoan/ch12_02_gbm_comparison.py)
