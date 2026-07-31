---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch25_README.md]
---

# Live Trading Systems

Live trading is where backtest assumptions become operational reality. The dominant failure mode is often not missing edge, but divergence between research and production systems.

## Core Requirements

- Same deterministic strategy logic in backtest, paper, live
- Event-driven live engine
- Broker adapters with explicit semantics
- Order state machine
- Pipeline parity verification
- SafeBroker-style risk controls
- Shadow mode, kill switch, reconciliation

## Staged Rollout

1. Backtest parity
2. Paper trading parity
3. Shadow live run
4. Small-capital rollout
5. Runtime monitoring + reconciliation
6. Kill switch and operator escalation

## Links

- [[unified-backtest-live-framework]]
- [[broker-integration-live-trading]]
- [[order-lifecycle-state-machine]]
- [[pipeline-verification-live]]
- [[runtime-safety-risk-controls]]
- [[strategy-simulation-backtesting]]
- [[risk-management-ml]]

## Sources

- [ch25_README.md](../../raw/articles/chung-khoan/ch25_README.md)
- [[ch25-live-trading]]
