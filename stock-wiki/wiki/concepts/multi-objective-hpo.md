---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_06_optuna_multi_asset.py]
---

# Multi-Objective HPO (IC vs Turnover)

Optuna multi-objective optimization: tối ưu cả Information Coefficient (predictive power) lẫn turnover (transaction cost) — hai objectives thường conflicting (high IC thường đi kèm high turnover).

## Pareto Front

Không có single best model — có tập models trên Pareto frontier. Practitioner chọn điểm trên frontier dựa trên risk/cost tolerance.

## Cross-Asset Transfer

NB06 kiểm tra hyperparameter transfer: parameters tối ưu trên ETFs có transfer được sang CME futures không? Kết quả giúp quyết định: nên tune per asset hay dùng global params.

## Links

- [[optuna-hyperparameter-tuning]]
- [[gradient-boosting-trading]]
- [[ml-backtest-baseline]]
- [[feature-selection-dedup]]

## Sources

- [ch12_06_optuna_multi_asset.py](../../raw/articles/chung-khoan/ch12_06_optuna_multi_asset.py)
