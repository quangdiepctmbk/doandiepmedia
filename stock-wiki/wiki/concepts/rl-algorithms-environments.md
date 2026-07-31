---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch21_01_algorithms_comparison.py
  - raw/articles/chung-khoan/ch21_02_optimal_execution_ppo.py
  - raw/articles/chung-khoan/ch21_03_market_making_ppo.py
  - raw/articles/chung-khoan/ch21_04_crypto_execution_rl.py
  - raw/articles/chung-khoan/ch21_rl_environments.py
  - raw/articles/chung-khoan/ch21_rl_calibration.py
---

# RL Algorithms & Environments for Trading

RL algorithm selection depends on action-space structure, sample efficiency, and stability requirements.

## Algorithm Comparison (NB01)

- **DQN** (value-based): discrete actions — good for simple trading signals
- **PPO** (actor-critic, on-policy): continuous actions — stable, sample-efficient
- **A2C** (actor-critic baseline): simpler but less stable

## Applications

- **PPO Execution** (NB02): minimize implementation shortfall in dynamic markets
- **PPO Market Making** (NB03): inventory-aware quoting vs Avellaneda-Stoikov
- **Crypto RL** (NB04): real perpetual futures data — execution on live markets
- **Environments**: rl_environments.py + rl_calibration.py — shared MDP construction utilities

## Links

- [[rl-execution-hedging]]
- [[ppo-optimal-execution]]
- [[market-making-rl]]
- [[deep-hedging-rl]]
- [[inverse-rl-trading]]
- [[sim-to-real-gap]]

## Sources

- [ch21_01_algorithms_comparison.py](../../raw/articles/chung-khoan/ch21_01_algorithms_comparison.py)
- [ch21_02_optimal_execution_ppo.py](../../raw/articles/chung-khoan/ch21_02_optimal_execution_ppo.py)
- [ch21_03_market_making_ppo.py](../../raw/articles/chung-khoan/ch21_03_market_making_ppo.py)
- [ch21_04_crypto_execution_rl.py](../../raw/articles/chung-khoan/ch21_04_crypto_execution_rl.py)
- [ch21_rl_environments.py](../../raw/articles/chung-khoan/ch21_rl_environments.py)
- [ch21_rl_calibration.py](../../raw/articles/chung-khoan/ch21_rl_calibration.py)
