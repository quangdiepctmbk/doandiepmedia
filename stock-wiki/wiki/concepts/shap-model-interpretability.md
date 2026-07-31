---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_05_shap_analysis.py
---

# SHAP Interpretability for Trading Models

SHAP (SHapley Additive exPlanations) decomposes a model's prediction into feature contributions. For linear models, SHAP values are exact: φⱼ = βⱼ · (xⱼ − x̄ⱼ).

## Why It Matters for Trading (Ch11)

SHAP is not cosmetic — it's part of model validation:
- Does the model learn economically sensible relationships?
- Are attributions stable across walk-forward folds?
- Do wrong high-conviction predictions share a feature pattern?

NB05 applies SHAP to Ridge regression on ETF features from Ch8, demonstrating exact decomposition for linear models and visual diagnostics for feature importance stability.

## Links

- [[ml-pipeline-trading]]
- [[regularized-regression-trading]]
- [[feature-selection-dedup]]
- [[robustness-sensitivity-analysis]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_05_shap_analysis.py](../../raw/articles/chung-khoan/ch11_05_shap_analysis.py)
