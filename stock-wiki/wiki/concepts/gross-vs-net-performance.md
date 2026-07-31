---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch18_10_gross_vs_net_performance.py
  - raw/articles/chung-khoan/ch18_11_cost_cliff.py
  - raw/articles/chung-khoan/ch18_09_frequency_tradeoff.py
---

# Gross vs Net & the Cost Cliff

Ultimate reality check: compare gross (theoretical) vs net (realized) strategy performance.

## Gross vs Net (NB10)

Framework for analyzing the gap: implementation shortfall decomposition, regime-aware benchmarking.

## Cost Cliff (NB11)

Intraday strategies that look stellar gross often become unprofitable after realistic costs. Dramatic impact — many strategies die at the cost cliff.

## Frequency Tradeoff (NB09)

Higher trading frequency → higher signal quality (shorter horizon) → higher turnover → higher costs. Optimal frequency minimizes net loss.

## Links

- [[transaction-costs-ml]]
- [[cost-taxonomy-asset-class]]
- [[almgren-chriss-execution]]
- [[transaction-cost-analysis]]

## Sources

- [ch18_09_frequency_tradeoff.py](../../raw/articles/chung-khoan/ch18_09_frequency_tradeoff.py)
- [ch18_10_gross_vs_net_performance.py](../../raw/articles/chung-khoan/ch18_10_gross_vs_net_performance.py)
- [ch18_11_cost_cliff.py](../../raw/articles/chung-khoan/ch18_11_cost_cliff.py)
