---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch16_09_performance_reporting.py]
---

# Performance Reporting Framework

The core metric set that every backtest report must include for credibility.

## Core Metrics

- Gross returns vs net returns (after costs)
- Annualized return, volatility, Sharpe ratio (+ confidence interval)
- Maximum drawdown, drawdown duration
- Turnover (one-way, round-trip)
- Win rate, profit factor, average trade PnL
- Baseline comparison (vs buy-and-hold, vs ETF baseline)
- Cost sensitivity (how does Sharpe change with cost assumption?)
- Regime-sliced: performance by volatility/trend states

## Insistence

Gross vs net results, Sharpe uncertainty, turnover, and baseline comparisons all belong in the same report.

## Links

- [[strategy-simulation-backtesting]]
- [[regime-backtest-diagnostics]]
- [[cost-sensitivity-analysis]]
- [[deflated-sharpe-ratio]]
- [[ml-backtest-baseline]]

## Sources

- [ch16_09_performance_reporting.py](../../raw/articles/chung-khoan/ch16_09_performance_reporting.py)
