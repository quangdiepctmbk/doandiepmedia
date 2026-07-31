---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch16_README.md]
---

# Strategy Simulation & Backtesting

Backtesting as a falsification discipline: a structured attempt to prove a strategy fails under realistic assumptions, not proof that it works.

## Core Disciplines

- **Trading Protocol**: specify timing, rebalancing, sizing, fills, costs, constraints
- **Vectorized vs Event-Driven**: array-based vs sequential simulation — different semantics, neither universally superior
- **Non-ML Baseline**: transparent ETF strategy before ML models (NB04)
- **Performance Reporting Stack**: gross/net returns, drawdown, turnover, baseline comparison, cost sensitivity (NB09)
- **Regime Diagnostics**: slice across volatility/trend states (NB10)
- **Search-Aware Inference**: DSR (NB12), RAS protocol (NB13) — account for multiple testing

## Key Idea

Prediction quality ≠ trading quality. IC alone is insufficient for deployable strategy selection.

## Links

- [[backtest-trading-protocol]]
- [[vectorized-vs-event-driven]]
- [[performance-reporting-framework]]
- [[regime-backtest-diagnostics]]
- [[deflated-sharpe-ratio]]
- [[ras-protocol]]
- [[cost-sensitivity-analysis]]
- [[engine-parity-backtest]]
- [[ml-backtest-baseline]]

## Sources

- [ch16_README.md](../../raw/articles/chung-khoan/ch16_README.md)
- [[ch16-strategy-simulation]]
