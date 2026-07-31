---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch16_03_single_asset_vectorbt.py
  - raw/articles/chung-khoan/ch16_04_single_asset_ml4t_backtest.py
  - raw/articles/chung-khoan/ch16_05_stateful_strategies.py
---

# Vectorized vs Event-Driven Backtesting

Two simulation paradigms with different semantics. Neither universally superior — appropriate for different research stages.

## Vectorized (Array-Based)

- Efficient for single-pass signal evaluation
- Assumes full path known upfront
- No state dependence (no conditional orders based on position)
- Best for: signal research, feature evaluation

## Event-Driven (Sequential)

- Bar-by-bar simulation with order book state
- Handles cash release, fill sequencing, stop-losses
- State-dependent strategies (trailing stops, VWAP, iceberged orders)
- Best for: production validation, high-frequency, complex execution

NB03 (VectorBT) vs NB04 (ml4t-backtest) vs NB05 (stateful patterns).

## Links

- [[strategy-simulation-backtesting]]
- [[backtest-trading-protocol]]
- [[engine-parity-backtest]]
- [[stateful-strategy-patterns]]

## Sources

- [ch16_03_single_asset_vectorbt.py](../../raw/articles/chung-khoan/ch16_03_single_asset_vectorbt.py)
- [ch16_04_single_asset_ml4t_backtest.py](../../raw/articles/chung-khoan/ch16_04_single_asset_ml4t_backtest.py)
- [ch16_05_stateful_strategies.py](../../raw/articles/chung-khoan/ch16_05_stateful_strategies.py)
