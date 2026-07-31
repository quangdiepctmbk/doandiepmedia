---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch25_01_unified_framework_demo.py
  - raw/articles/chung-khoan/ch25_02_etfs_deployment_loop.py
  - raw/articles/chung-khoan/ch25__etfs_features.py
---

# Unified Backtest-Live Framework

A unified framework runs identical strategy code in backtest, paper, and live modes, eliminating two-pipeline divergence bugs.

## NB01 Unified Framework Demo

- Dual moving-average crossover strategy
- Same `Strategy` class through `ml4t.backtest.Engine` and `ml4t.live.LiveEngine`
- 9/9 signal parity proof
- Demonstrates zero-code-change deployment claim

## NB02 ETF Deployment Loop

Six-step deployment cycle:

1. Refresh ETF data via `ml4t-data`
2. Recompute financial-only feature subset
3. Refit Ridge regressor with α=10⁶
4. Predict live window
5. Route basket through both engines for parity
6. Persist run record for monitoring

## Links

- [[live-trading-systems]]
- [[pipeline-verification-live]]
- [[ml-backtest-baseline]]
- [[strategy-simulation-backtesting]]

## Sources

- [ch25_01_unified_framework_demo.py](../../raw/articles/chung-khoan/ch25_01_unified_framework_demo.py)
- [ch25_02_etfs_deployment_loop.py](../../raw/articles/chung-khoan/ch25_02_etfs_deployment_loop.py)
- [ch25__etfs_features.py](../../raw/articles/chung-khoan/ch25__etfs_features.py)
