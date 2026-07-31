---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch18_README.md]
---

# Transaction Costs in ML Trading

Costs are a workflow constraint, not a backtest adjustment. Many strategies fail because the implementation problem was ignored.

## Taxonomy

- **Explicit**: commissions, exchange fees, settlement, stamp duty
- **Implicit**: bid-ask spread, slippage, market impact
- **Capacity**: how much can be traded before impact degrades alpha

## Cost Model Ladder

1. Spread-only (simplest, optimistic)
2. Linear slippage (fixed bps)
3. Square-root impact (Almgren-Chriss, Kyle's lambda)
4. Full microstructure simulation

## Key Rule

Breakeven turnover, minimum required edge, alpha-to-go, capacity analysis, kill criteria — treat these as mandatory decision rules.

## Links

- [[cost-taxonomy-asset-class]]
- [[spread-estimation]]
- [[market-impact-calibration]]
- [[almgren-chriss-execution]]
- [[vwap-twap-execution]]
- [[ml-dynamic-execution]]
- [[cost-model-benchmark]]
- [[gross-vs-net-performance]]
- [[cost-cliff-intraday]]
- [[execution-frequency-tradeoff]]
- [[transaction-cost-analysis]]
- [[ml-backtest-baseline]]

## Sources

- [ch18_README.md](../../raw/articles/chung-khoan/ch18_README.md)
- [[ch18-transaction-costs]]
