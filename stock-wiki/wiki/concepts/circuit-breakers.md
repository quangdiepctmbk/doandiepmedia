---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch26_04_circuit_breakers.py
---

# Circuit Breakers for Trading Systems

Automated safety protection with multi-level circuit breakers.

## NB04 — Four-Breaker State Machine

- Drawdown breaker
- Daily-loss breaker
- Consecutive-loss breaker
- Latency breaker

Lifecycle: CLOSED → OPEN → HALF_OPEN transitions
Shared manager event log
Driven by real SPY 2020 H1 COVID crash path

## Links

- [[mlops-governance-trading]]
- [[runtime-safety-risk-controls]]
- [[live-trading-systems]]
- [[risk-management-ml]]
- [[drift-monitoring-performance]]
- [[safe-model-rollout]]

## Sources

- [ch26_04_circuit_breakers.py](../../raw/articles/chung-khoan/ch26_04_circuit_breakers.py)
