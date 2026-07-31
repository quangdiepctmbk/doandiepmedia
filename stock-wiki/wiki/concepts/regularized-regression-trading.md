---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_02_regularization_paths.py
---

# Regularized Regression for Trading

Regularized regression applies Ridge (L2), LASSO (L1), and Elastic Net (L1+L2) to financial return prediction, replacing plain OLS when features are numerous, correlated, and noisy.

## Key Findings (Ch11)

- **Ridge** outperforms LASSO/Elastic Net on most case studies — financial return signal is diffuse across many features, not sparse
- **LASSO** useful when feature selection is a goal (interpretability, reduced rotation)
- **Elastic Net** hybrid — rarely beats Ridge on pure IC but improves stability
- All regularized models use walk-forward CV with leakage-safe standardization

## Leakage-Safe Standardization

Standardization (mean, std) must be fit only inside each training window and applied to test/unseen data. This applies to all preprocessing steps: scaling, outlier capping, missing imputation.

## Links

- [[ml-pipeline-trading]]
- [[leakage-safe-preprocessing]]
- [[hyperparameter-tuning-validation-bias]]
- [[walk-forward-evaluation]]
- [[feature-selection-dedup]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_02_regularization_paths.py](../../raw/articles/chung-khoan/ch11_02_regularization_paths.py)
