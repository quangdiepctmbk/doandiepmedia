---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch25_README.md
ingested: 2026-07-26
related_raw:
  - ch25_01_unified_framework_demo.py
  - ch25_02_etfs_deployment_loop.py
  - ch25_03_ib_paper_trading_demo.py
  - ch25_04_alpaca_paper_trading_demo.py
  - ch25_05_alpaca_crypto_live_demo.py
  - ch25_06_quantconnect_case_study.py
  - ch25_07_order_state_machine.py
  - ch25_08_pipeline_verification.py
  - ch25_09_crypto_funding_deployment_loop.py
  - ch25_10_safety_risk_demo.py
  - ch25_11_fx_deployment_loop.py
  - ch25_12_ib_basket_rebalance_demo.py
  - ch25_13_runtime_safety_showcase.py
  - ch25__etfs_features.py
  - ch25_async_utils.py
  - ch25_demo_artifacts.py
---

# Live Trading Systems — Chương 25 (ML4T)

## Summary

Chương 25 xử lý đoạn khó nhất: chuyển profitable backtest sang live execution. Thông điệp chính: nhiều strategy fail vì **production system diverges from research environment**, không nhất thiết vì thiếu edge. Unified framework giảm rủi ro bằng cách chạy cùng strategy code trong backtest, paper, và live modes.

13 notebooks + 3 support modules + README.

### Sections (7)

1. **25.1 Unified Framework Advantage** — same strategy code across backtest/live; parity proof (NB01–02)
2. **25.2 Interactive Brokers Integration** — IBKR paper, SafeBroker, startup reconciliation, basket rebalance (NB03, NB12)
3. **25.3 Alpaca Integration** — equities/ETFs/crypto, REST/WebSocket, paper + live crypto demos (NB04–05)
4. **25.4 QuantConnect Managed Platform** — prediction export bridge to LEAN (NB06)
5. **25.5 Order Lifecycle Management** — stateful async order FSM, partial fills/cancel/reject/idempotent recovery (NB07)
6. **25.6 Pipeline Verification** — parity tests from raw data → features → predictions → sizing → orders (NB08–09, NB11)
7. **25.7 Operational Readiness** — SafeBroker risk controls, kill switch, shadow mode, runtime health (NB10, NB13)

### Key Takeaways

- Live trading risk is often **technical divergence**, not strategy edge.
- Use a dual-mode event-driven architecture where deterministic strategy logic is unchanged across modes.
- Broker adapters differ: IBKR multi-asset power, Alpaca lower friction, QuantConnect managed platform trade-offs.
- Order handling needs a formal state machine and idempotent crash recovery.
- Deployment requires staged rollout: pre-flight checks, shadow trading, kill switches, reconciliation.
- Pipeline parity distinguishes market changes from software bugs.

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 25
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/25_live_trading)
- [[ch24-autonomous-agents]] (previous chapter)
