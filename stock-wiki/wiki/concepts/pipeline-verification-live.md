---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch25_08_pipeline_verification.py
  - raw/articles/chung-khoan/ch25_09_crypto_funding_deployment_loop.py
  - raw/articles/chung-khoan/ch25_11_fx_deployment_loop.py
---

# Live Pipeline Verification

Pipeline verification proves that backtest and live paths agree from raw data through orders. Without this, live underperformance cannot be diagnosed as market change versus software bug.

## NB08 Parity Tests

- 5 gated parity tests + 1 expected difference
- Data, features, predictions, sizing, and order parity
- Deterministic synthetic tape with static symbol offsets
- CI-compatible pass/fail summary
- Explicit SKIP semantics instead of silent pass on empty live logs

## NB09 Crypto Funding Deployment Loop

- OKX public BTC-USDT-SWAP data
- Ch12 crypto funding feature schema
- 3-iteration paper trading loop
- Parity with regime stress case

## NB11 FX Deployment Loop

- IB paper as both data plane and execution plane
- Momentum/carry/USD-factor features matching Ch12 FX schema
- Daily paper rebalance loop

## Links

- [[live-trading-systems]]
- [[unified-backtest-live-framework]]
- [[broker-integration-live-trading]]
- [[strategy-synthesis-pipeline]]

## Sources

- [ch25_08_pipeline_verification.py](../../raw/articles/chung-khoan/ch25_08_pipeline_verification.py)
- [ch25_09_crypto_funding_deployment_loop.py](../../raw/articles/chung-khoan/ch25_09_crypto_funding_deployment_loop.py)
- [ch25_11_fx_deployment_loop.py](../../raw/articles/chung-khoan/ch25_11_fx_deployment_loop.py)
