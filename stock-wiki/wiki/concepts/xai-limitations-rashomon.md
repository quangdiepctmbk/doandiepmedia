---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_09_xai_limitations.py]
---

# XAI Limitations: Rashomon Effect

XAI instability hiện tượng: các models cho predictions gần giống nhau nhưng SHAP explanations khác nhau đáng kể (Rashomon set).

## Key Lesson

SHAP values are not unique — có nhiều bộ SHAP explanations khác nhau cho cùng prediction accuracy. Điều này đặc biệt quan trọng trong trading khi dùng SHAP để:

- Debug model decisions
- Justify feature usage for compliance
- Determine feature pruning
- Monitor drift

NB09 demonstrates: các nominally equivalent fits (similar val loss, similar IC) produce systematically different SHAP attributions.

## Links

- [[treeshap-interpretability]]
- [[shap-model-interpretability]]
- [[gradient-boosting-trading]]
- [[robustness-sensitivity-analysis]]

## Sources

- [ch12_09_xai_limitations.py](../../raw/articles/chung-khoan/ch12_09_xai_limitations.py)
