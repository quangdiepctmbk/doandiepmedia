---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch16_01_backtest_first_principles.py]
---

# Backtest Trading Protocol

A backtest must specify every component of the trading protocol before results become interpretable.

## Protocol Components

- Signal timing (when are signals generated?)
- Execution assumptions (fill at close/next-open/slippage model?)
- Rebalancing schedule (daily/weekly/monthly?)
- Position sizing (fixed/pct/Kelly/volatility-target?)
- Transaction costs (commission, spread, market impact)
- Constraints (max position, max sector, margin)
- Benchmark choice

Many published disagreements are really disagreements about protocol rather than signal quality.

NB01 implements from first principles: from returns to portfolio simulation.

## Links

- [[strategy-simulation-backtesting]]
- [[vectorized-vs-event-driven]]
- [[cost-sensitivity-analysis]]
- [[performance-reporting-framework]]
- [[ml-backtest-baseline]]

## Sources

- [ch16_01_backtest_first_principles.py](../../raw/articles/chung-khoan/ch16_01_backtest_first_principles.py)
