---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch12_04_optuna_tuning.py
  - raw/articles/chung-khoan/ch12_05_cross_library_hpo.py
  - raw/articles/chung-khoan/ch12_07_hpo_comparison.py
---

# Optuna Hyperparameter Tuning for GBMs

Optuna với Bayesian optimization (TPE) cho GBM hyperparameter tuning, bao gồm pruning, walk-forward validation, và fANOVA analysis.

## Key Methods

- **TPE (Tree-structured Parzen Estimator)**: thay thế grid search/random search
- **Pruning**: early-stop unpromising trials (MedianPruner, Hyperband)
- **Walk-forward HPO**: each Optuna trial runs expanding window CV — slower but less biased
- **fANOVA**: functional ANOVA để đo feature importance của HPO search space
- **Multi-objective**: IC và turnover cùng lúc → Pareto front (NB06)

## Single-loop vs Walk-forward HPO

NB04 quantifies: single-fold HPO overestimates performance vs walk-forward. NB07 shows TPE beats grid search at equal compute budget.

## Links

- [[gradient-boosting-trading]]
- [[hyperparameter-tuning-validation-bias]]
- [[multi-objective-hpo]]
- [[walk-forward-evaluation]]

## Sources

- [ch12_04_optuna_tuning.py](../../raw/articles/chung-khoan/ch12_04_optuna_tuning.py)
- [ch12_05_cross_library_hpo.py](../../raw/articles/chung-khoan/ch12_05_cross_library_hpo.py)
- [ch12_07_hpo_comparison.py](../../raw/articles/chung-khoan/ch12_07_hpo_comparison.py)
