---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch21_README.md]
---

# RL for Execution and Hedging

RL phù hợp cho financial sequential control problems: execution, market making, hedging. Supervised learning = prediction; RL = what to do next when actions affect outcomes.

## Applications

- **Optimal Execution**: minimize implementation shortfall vs TWAP/AC (NB02, NB04)
- **Market Making**: inventory-aware quoting, spread/skew placement (NB03)
- **Deep Hedging**: risk measure of terminal PnL under costs (NB05)
- **Inverse RL**: infer objectives from observed behavior (NB06)

## Key Challenges

- **Sim-to-real gap**: non-stationarity, impact reflexivity, latency, poor fills (NB07)
- **Reward hacking**: poorly specified reward → undesirable behavior
- **Partial observability**: state engineering + recurrent models essential
- **Benchmark mismatch**: must beat TWAP/AC/baselines, not just look good

## Links

- [[rl-algorithms-comparison]]
- [[ppo-optimal-execution]]
- [[market-making-rl]]
- [[deep-hedging-rl]]
- [[inverse-rl-trading]]
- [[sim-to-real-gap]]
- [[almgren-chriss-execution]]
- [[transaction-costs-ml]]

## Sources

- [ch21_README.md](../../raw/articles/chung-khoan/ch21_README.md)
- [[ch21-rl-execution-hedging]]
