---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch15_02_dowhy_causal_graph.py]
---

# Causal Validation & Refutation

DoWhy-based validation workflow: specify DAG → identify estimand → estimate → refute. A causal claim must survive multiple falsification checks (but can never be proven).

## Refutation Battery (Ch15)

- **Placebo test**: replace treatment with random noise — effect should go to zero
- **Negative control**: use an outcome that shouldn't be affected
- **Sensitivity analysis**: how strong must omitted confounding be to overturn the result?
- **Subset stability**: does effect hold across train/test splits?
- **Block permutation**: shuffle treatment within blocks (preserving time dependence)

NB02 demonstrates full DoWhy validation on crypto funding-rate, comparing two outcomes (forward returns vs premium reversion) — showing outcome choice determines credibility.

## Links

- [[causal-ml-trading]]
- [[double-machine-learning]]
- [[bsts-event-study]]
- [[evidence-boundary]]
- [[multiple-testing-selection-bias]]

## Sources

- [ch15_02_dowhy_causal_graph.py](../../raw/articles/chung-khoan/ch15_02_dowhy_causal_graph.py)
