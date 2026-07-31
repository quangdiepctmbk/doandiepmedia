---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch25_03_ib_paper_trading_demo.py
  - raw/articles/chung-khoan/ch25_04_alpaca_paper_trading_demo.py
  - raw/articles/chung-khoan/ch25_05_alpaca_crypto_live_demo.py
  - raw/articles/chung-khoan/ch25_06_quantconnect_case_study.py
  - raw/articles/chung-khoan/ch25_11_fx_deployment_loop.py
  - raw/articles/chung-khoan/ch25_12_ib_basket_rebalance_demo.py
---

# Broker Integration for Live Trading

Broker and platform choice determines asset coverage, execution quality, operational burden, and how much of the research pipeline must be reimplemented.

## Interactive Brokers (NB03, NB11, NB12)

- Multi-asset coverage
- TWS/Gateway connection management
- Startup reconciliation via `SafeBroker.connect()`
- IB basket rebalance workflow with persisted state
- FX deployment loop uses same IB session for data plane and execution plane

## Alpaca (NB04, NB05)

- Lower-friction deployment for US equities/ETFs/crypto
- REST/WebSocket APIs
- Paper trading workflow and crypto live demo
- Crypto universe mapping: Binance USDT perps → Alpaca USD spot subset

## QuantConnect (NB06)

- Managed platform trade-offs
- Prediction export bridge to LEAN
- Avoids reimplementing feature engineering inside QuantConnect

## Links

- [[live-trading-systems]]
- [[runtime-safety-risk-controls]]
- [[order-lifecycle-state-machine]]
- [[pipeline-verification-live]]

## Sources

- [ch25_03_ib_paper_trading_demo.py](../../raw/articles/chung-khoan/ch25_03_ib_paper_trading_demo.py)
- [ch25_04_alpaca_paper_trading_demo.py](../../raw/articles/chung-khoan/ch25_04_alpaca_paper_trading_demo.py)
- [ch25_05_alpaca_crypto_live_demo.py](../../raw/articles/chung-khoan/ch25_05_alpaca_crypto_live_demo.py)
- [ch25_06_quantconnect_case_study.py](../../raw/articles/chung-khoan/ch25_06_quantconnect_case_study.py)
- [ch25_11_fx_deployment_loop.py](../../raw/articles/chung-khoan/ch25_11_fx_deployment_loop.py)
- [ch25_12_ib_basket_rebalance_demo.py](../../raw/articles/chung-khoan/ch25_12_ib_basket_rebalance_demo.py)
