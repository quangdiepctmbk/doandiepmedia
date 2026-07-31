---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch15_10_case_study_insights.py]
---

# Causal Case Study Insights

Cross-dataset DML synthesis: scores each primary treatment across 9 case studies against two gates — HAC significance and block-permutation refutation.

## Key Findings

- **Confounding bias pervasive**: naive OLS estimates shrink or disappear after DML
- **Predictive power ≠ causal effect**: many features predict returns but fail refutation
- **HAC significance ≠ refutation survival**: some HAC-significant effects fail block-permutation
- Multi-horizon analysis shows effect decay patterns
- Implication for portfolio construction: weight factors by causal confidence (Ch17)

## Links

- [[causal-ml-trading]]
- [[double-machine-learning]]
- [[causal-validation-refutation]]
- [[ml-backtest-baseline]]
- [[evidence-boundary]]

## Sources

- [ch15_10_case_study_insights.py](../../raw/articles/chung-khoan/ch15_10_case_study_insights.py)
