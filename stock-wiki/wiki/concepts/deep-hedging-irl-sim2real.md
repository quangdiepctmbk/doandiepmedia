---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch21_05_deep_hedging_pfhedge.py
  - raw/articles/chung-khoan/ch21_06_inverse_reinforcement_learning.py
  - raw/articles/chung-khoan/ch21_07_backtest_with_impact.py
---

# Deep Hedging, Inverse RL & Sim-to-Real

Advanced RL topics: deep hedging trừ derivatives, IRL infer objectives, và sim-to-real gap.

## Deep Hedging (NB05, pfhedge)

- Neural network learns hedging policy minimizing CVaR/P&L distribution under transaction costs
- Benchmark: delta hedging, Whalley-Wilmott
- Friction-aware risk control > analytical replication

## Inverse RL (NB06)

- Infer reward functions from observed expert behavior
- Distinguish IRL from behavior cloning: reward inference generalizes better
- Limitations: identifiability, demonstration quality, model assumptions

## Sim-to-Real Gap (NB07)

- **Non-stationarity**: training distribution ≠ live distribution
- **Impact reflexivity**: execution changes the market
- **Latency**: fills at stale prices
- **Reward hacking**: agent exploits simulator flaws
- **Solutions**: offline RL, off-policy evaluation, staged deployment, governance

## Links

- [[rl-execution-hedging]]
- [[rl-algorithms-environments]]
- [[almgren-chriss-execution]]
- [[transaction-cost-analysis]]

## Sources

- [ch21_05_deep_hedging_pfhedge.py](../../raw/articles/chung-khoan/ch21_05_deep_hedging_pfhedge.py)
- [ch21_06_inverse_reinforcement_learning.py](../../raw/articles/chung-khoan/ch21_06_inverse_reinforcement_learning.py)
- [ch21_07_backtest_with_impact.py](../../raw/articles/chung-khoan/ch21_07_backtest_with_impact.py)
