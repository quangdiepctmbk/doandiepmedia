---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch12_08_shap_analysis.py
  - raw/articles/chung-khoan/ch12_10_shap_nlp_sentiment.py
---

# TreeSHAP Interpretability

TreeSHAP extends SHAP to tree ensembles (XGBoost, LightGBM, CatBoost) — exact, fast, and decomposable into main effects and interactions.

## Capabilities (Ch12)

- **Global explanation**: mean |SHAP| per feature across all predictions
- **Local explanation**: SHAP waterfall for single predictions
- **Interaction decomposition**: SHAP interaction values capture pairwise effects
- **Walk-forward drift**: monitor SHAP distributions across folds → detect feature relationships changing over time
- **SHAP-based feature selection**: remove low-importance features, monitor IC impact
- **NLP token-level attribution**: NB10 applies SHAP to FinBERT sentiment → token-level word importance

## Comparison

MDI (mean decrease impurity), PFI (permutation), SHAP — ideal is consensus between all three. SHAP is the most stable and interpretable.

## Links

- [[gradient-boosting-trading]]
- [[shap-model-interpretability]]
- [[xai-limitations-rashomon]]
- [[feature-selection-dedup]]

## Sources

- [ch12_08_shap_analysis.py](../../raw/articles/chung-khoan/ch12_08_shap_analysis.py)
- [ch12_10_shap_nlp_sentiment.py](../../raw/articles/chung-khoan/ch12_10_shap_nlp_sentiment.py)
