---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch15_README.md]
---

# Causal ML for Trading

Causal ML answers harder questions than prediction: does factor X cause returns, or is the relationship driven by confounders? The chapter covers three causal problem types with corresponding estimators.

## Three Questions, Three Estimators

| Question | Estimator | Library |
|----------|-----------|---------|
| Continuous treatment effect? | Double Machine Learning | EconML |
| Discrete event impact? | Bayesian Structural Time-Series | tfcausalimpact |
| Unknown causal structure? | PCMCI, NOTEARS, VAR-LiNGAM | Tigramite, causal-learn |

## Core Disciplines

- Specify treatment, outcome, estimand, counterfactual via DAG
- Choose admissible adjustment set (backdoor criterion)
- Validate and refute: placebo tests, sensitivity analysis, subset stability
- Sophisticated estimator cannot rescue identification failure

## Links

- [[double-machine-learning]]
- [[bsts-event-study]]
- [[causal-discovery-methods]]
- [[causal-validation-refutation]]
- [[factor-zoo-validation]]
- [[causal-case-study-insights]]
- [[evidence-boundary]]

## Sources

- [ch15_README.md](../../raw/articles/chung-khoan/ch15_README.md)
- [[ch15-causal-estimation]]
