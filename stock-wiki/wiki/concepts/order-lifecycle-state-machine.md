---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch25_07_order_state_machine.py]
---

# Order Lifecycle State Machine

Live execution is a stateful async process. Orders require formal state machines to handle partial fills, cancellations, rejections, race conditions, and crash recovery.

## NB07

Implements:

- 10 order states
- 19 valid state-event transitions
- Audit trail logging
- Invalid transition rejection
- PENDING_CANCEL → FILLED race handling
- Weighted-average fill price calculation

## Why It Matters

Backtests often assume immediate fills. Live systems must represent the actual lifecycle of intent → submitted → acknowledged → partial/filled/rejected/cancelled, with idempotent recovery if the process restarts.

## Links

- [[live-trading-systems]]
- [[broker-integration-live-trading]]
- [[runtime-safety-risk-controls]]
- [[almgren-chriss-execution]]

## Sources

- [ch25_07_order_state_machine.py](../../raw/articles/chung-khoan/ch25_07_order_state_machine.py)
