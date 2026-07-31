---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_04_nested_cv_hpo.py
---

# Hyperparameter Tuning & Validation Bias

Hyperparameter tuning on time series requires nested cross-validation (or walk-forward equivalent) to avoid selection bias inflation.

## Single-Loop vs Nested CV

- **Single-loop CV**: tune HPO on the same validation set used for performance reporting → optimistically biased
- **Nested CV**: inner loop for HPO, outer loop for performance estimation → unbiased evaluation

NB04 demonstrates on an alpha-grid sweep + Optuna: single-loop inflation is material and measurable. For trading, the walk-forward equivalent is: tune HPO on expanding windows, evaluate on sealed holdout.

## Links

- [[regularized-regression-trading]]
- [[ml-pipeline-trading]]
- [[walk-forward-evaluation]]
- [[multiple-testing-selection-bias]]
- [[train-only-preprocessing]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_04_nested_cv_hpo.py](../../raw/articles/chung-khoan/ch11_04_nested_cv_hpo.py)
