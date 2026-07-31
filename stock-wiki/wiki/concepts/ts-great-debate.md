---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_03_great_debate.py]
---

# The Great Debate: Transformers vs Simple Baselines

The "Great Debate" (Zeng et al. 2022, "Are Transformers Effective for Time Series?") showed simple linear baselines embarrassing many Transformer variants on established forecasting benchmarks.

## Core Critique

- Many TS Transformer papers compared against weak or outdated baselines
- When compared fairly, simple **linear models (DLinear, NLinear)** matched or beat elaborate Transformer architectures
- This raised standards: any new TS model must beat linear baselines first

NB03 replicates this critique on financial data: does attention structure actually help for ETF return prediction?

## Resolution

Modern TS Transformers (PatchTST, iTransformer) were designed specifically to address these critiques — patching and proper multivariate handling.

## Links

- [[time-series-transformers]]
- [[dl-time-series-forecasting]]
- [[regularized-regression-trading]]
- [[ml-backtest-baseline]]

## Sources

- [ch13_03_great_debate.py](../../raw/articles/chung-khoan/ch13_03_great_debate.py)
