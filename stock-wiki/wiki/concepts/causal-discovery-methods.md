---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch15_07_tigramite_time_series.py
  - raw/articles/chung-khoan/ch15_08_neural_causal_discovery.py
  - raw/articles/chung-khoan/ch15_09_adia_causal_benchmark.py
---

# Causal Discovery Methods

Causal discovery infers causal structure from observational data without pre-specified treatment/outcome. Ch15 covers four methods — all treated as **hypothesis generators**, not truth machines.

## Methods (Ch15)

- **PCMCI**: constraint-based + conditional independence tests (ParCorr). NB07 on GLD/IEF/SPY/VIX → null result (no stable lagged edges)
- **NOTEARS**: continuous optimization for DAG learning (Zheng et al. 2018). NB08 comparison on 7 ETFs
- **VAR-LiNGAM**: non-Gaussian SVAR (Hyvärinen et al. 2010). From scratch + causal-learn
- **Granger causality**: pairwise predictive causality — baseline, not structural

## Key Finding

Methods diverge wildly: from zero to dozens of edges on identical data. Block-bootstrap stability critical.

## Links

- [[causal-ml-trading]]
- [[double-machine-learning]]
- [[bsts-event-study]]
- [[causal-validation-refutation]]
- [[factor-zoo-validation]]

## Sources

- [ch15_07_tigramite_time_series.py](../../raw/articles/chung-khoan/ch15_07_tigramite_time_series.py)
- [ch15_08_neural_causal_discovery.py](../../raw/articles/chung-khoan/ch15_08_neural_causal_discovery.py)
- [ch15_09_adia_causal_benchmark.py](../../raw/articles/chung-khoan/ch15_09_adia_causal_benchmark.py)
