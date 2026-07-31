---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch25_10_safety_risk_demo.py
  - raw/articles/chung-khoan/ch25_13_runtime_safety_showcase.py
---

# Runtime Safety & Risk Controls

Operational readiness turns working code into a system safe enough to trade with money.

## SafeBroker Controls (NB10)

8 layers:

- Order size limits
- Position limits
- Daily-loss limits
- Rate limiting
- Asset restrictions
- Kill switch (persists across restarts)
- Shadow mode
- VirtualPortfolio with weighted-average cost basis

## Runtime Safety Showcase (NB13)

- Stale data rejection with `max_data_staleness_seconds`
- Automatic kill switch on daily-loss breach
- Kill-switch latch survives `SafeBroker` reconstruction
- Startup reconciliation against divergent persisted state
- `LiveEngine.runtime_status()` health transitions: stopped → ok → feed_silent
- `ml4t-live status` CLI walkthrough

## Links

- [[live-trading-systems]]
- [[risk-management-ml]]
- [[agent-evaluation-governance]]
- [[order-lifecycle-state-machine]]

## Sources

- [ch25_10_safety_risk_demo.py](../../raw/articles/chung-khoan/ch25_10_safety_risk_demo.py)
- [ch25_13_runtime_safety_showcase.py](../../raw/articles/chung-khoan/ch25_13_runtime_safety_showcase.py)
