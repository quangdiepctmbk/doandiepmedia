---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch16_05_stateful_strategies.py
  - raw/articles/chung-khoan/ch16_08_signal_method_comparison.py
  - raw/articles/chung-khoan/ch16_14_cost_sensitivity.py
---

# Stateful Strategies & Cost Sensitivity

Two practical concerns that separate research-grade backtests from production:

## Stateful Strategy Patterns (NB05)

Strategies that depend on internal state (position, entry price, trailing stop level) cannot be vectorized. NB05 covers:
- Trailing stops and take-profit
- VWAP execution with order book state
- Position-dependent rebalancing

## Signal Method Comparison (NB08)

Fixed threshold vs rolling percentile for generating trading signals from the same forecast.

## Cost Sensitivity (NB14)

How does Sharpe change with cost assumptions? A strategy viable at 5bps may fail at 15bps. Essential for ML4T: transaction costs can eliminate the edge of a positive-IC model.

## Links

- [[strategy-simulation-backtesting]]
- [[vectorized-vs-event-driven]]
- [[performance-reporting-framework]]
- [[cost-model-transaction-costs]]

## Sources

- [ch16_05_stateful_strategies.py](../../raw/articles/chung-khoan/ch16_05_stateful_strategies.py)
- [ch16_08_signal_method_comparison.py](../../raw/articles/chung-khoan/ch16_08_signal_method_comparison.py)
- [ch16_14_cost_sensitivity.py](../../raw/articles/chung-khoan/ch16_14_cost_sensitivity.py)
