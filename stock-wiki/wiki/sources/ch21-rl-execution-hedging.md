---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch21_README.md
ingested: 2026-07-26
related_raw:
  - ch21_rl_environments.py
  - ch21_rl_calibration.py
  - ch21_01_algorithms_comparison.py
  - ch21_02_optimal_execution_ppo.py
  - ch21_03_market_making_ppo.py
  - ch21_04_crypto_execution_rl.py
  - ch21_05_deep_hedging_pfhedge.py
  - ch21_06_inverse_reinforcement_learning.py
  - ch21_07_backtest_with_impact.py
---

# RL Execution and Hedging — Chương 21 (ML4T)

## Summary

Chương 21 dùng Reinforcement Learning cho execution, market making, và hedging. RL phù hợp khi task có objectives rõ ràng, feedback loop tight, và reward signal defensible — execution/hedging > alpha discovery.

7 notebooks + rl_environments.py + rl_calibration.py.

### Sections (8):

1. **21.1 Sequential Decision Paradigm**: RL = control (what to do next), not prediction
2. **21.2 Markets as MDPs**: state, action, reward, transition, discounting; partial observability critical
3. **21.3 Core Algorithms**: DQN vs PPO vs A2C — discrete vs continuous action spaces (NB01)
4. **21.4 Optimal Execution**: PPO agent minimizing implementation shortfall; crypto RL on real perpetual data (NB02, NB04)
5. **21.5 Market Making**: PPO inventory-aware quoting vs Avellaneda-Stoikov (NB03)
6. **21.6 Deep Hedging**: P&L distribution + tail risk under transaction costs (NB05)
7. **21.7 Inverse RL**: infer objectives from observed behavior — reward inference vs behavior cloning (NB06)
8. **21.8 Sim-to-Real Gap**: non-stationarity, impact reflexivity, latency, reward hacking — barriers to deployability (NB07)

### Key Takeaways

- **RL ≠ magic** — chỉ có lợi thế rõ cho sequential control problems
- **Sim-to-real gap** là rào cản lớn nhất: simulator fidelity, offline RL, staged deployment
- **Algorithms**: PPO cho continuous actions, DQN cho discrete, actor-critic chung
- **Execution**: RL beats TWAP/AC benchmarks khi môi trường dynamic
- **Market making**: learned inventory-aware quoting vs analytical baselines
- **Deep hedging**: risk measure of terminal PnL >> delta hedging dưới costs
- **IRL**: infer reward functions từ hành vi quan sát — nhưng giới hạn bởi identifiability

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 21
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/21_rl_execution_hedging)
- [[ch20-strategy-synthesis]] (previous chapter)
