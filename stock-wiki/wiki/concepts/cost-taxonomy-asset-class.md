---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch18_01_cost_taxonomy.py
  - raw/articles/chung-khoan/ch18_02_spread_estimation.py
  - raw/articles/chung-khoan/ch18_03_market_impact_calibration.py
---

# Cost Taxonomy, Spread & Market Impact

Mapping the transaction cost landscape across asset classes: exchange fee structures, spread regimes, breakeven alpha requirements.

## Key Components

- **Cost Taxonomy** (NB01): explicit vs implicit per asset class (cme_futures, crypto_perps, etfs et al.)
- **Spread Estimation** (NB02): Roll (1984) and Corwin-Schultz (2012) estimators from OHLCV, validated against microstructure data
- **Market Impact** (NB03): calibrate Kyle's lambda from NASDAQ-100 trade classification, intraday volume profiles, capacity limits
- **Commission vs Slippage** (NB12): 6 commission × 5 slippage models, 4 asset-class cost stacks, P&L & frequency sensitivity

## Links

- [[transaction-costs-ml]]
- [[almgren-chriss-execution]]
- [[cost-model-benchmark]]
- [[gross-vs-net-performance]]

## Sources

- [ch18_01_cost_taxonomy.py](../../raw/articles/chung-khoan/ch18_01_cost_taxonomy.py)
- [ch18_02_spread_estimation.py](../../raw/articles/chung-khoan/ch18_02_spread_estimation.py)
- [ch18_03_market_impact_calibration.py](../../raw/articles/chung-khoan/ch18_03_market_impact_calibration.py)
- [ch18_12_commission_slippage_comparison.py](../../raw/articles/chung-khoan/ch18_12_commission_slippage_comparison.py)
