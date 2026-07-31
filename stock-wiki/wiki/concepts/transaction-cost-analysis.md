---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch18_12_commission_slippage_comparison.py
  - raw/articles/chung-khoan/ch18__cost_analysis.py
---

# Transaction Cost Analysis (TCA) & Model Validation

Closes the loop: cost assumptions are hypotheses to test, decompose, and recalibrate against live evidence.

## TCA Components

- **Implementation shortfall**: actual fill price vs arrival benchmark
- **Decomposition**: impact + timing + opportunity cost
- **Regime-aware benchmarking**: costs vary by volatility/liquidity regimes
- **Recalibration**: adjust ex ante models based on ex post TCA

## Guardrails

- Breakeven turnover
- Minimum required edge
- Alpha-to-go (remaining edge after costs)
- Capacity analysis (max AUM before impact destroys alpha)
- Kill criteria: strategy viability thresholds

## Links

- [[transaction-costs-ml]]
- [[cost-taxonomy-asset-class]]
- [[gross-vs-net-performance]]
- [[cost-cliff-intraday]]
- [[almgren-chriss-execution]]

## Sources

- [ch18_12_commission_slippage_comparison.py](../../raw/articles/chung-khoan/ch18_12_commission_slippage_comparison.py)
- [ch18__cost_analysis.py](../../raw/articles/chung-khoan/ch18__cost_analysis.py)
