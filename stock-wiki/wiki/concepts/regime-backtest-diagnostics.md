---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch16_10_regime_backtest_analysis.py]
---

# Regime Backtest Diagnostics

Aggregate performance can be dangerously incomplete. Strategy's "good" overall statistics may be driven by favorable environments while economically painful losses concentrate in specific regimes.

## Regimes to Slice By (Ch16)

- Volatility regime (low / medium / high)
- Trend regime (bull / bear / sideways)
- Correlation regime (diversification breakdown periods)

NB10 applies regime-sliced diagnostics to the §16.4 ETF baseline, revealing when aggregate statistics are regime-driven.

## Links

- [[strategy-simulation-backtesting]]
- [[performance-reporting-framework]]
- [[cost-sensitivity-analysis]]
- [[deflated-sharpe-ratio]]
- [[ml-backtest-baseline]]

## Sources

- [ch16_10_regime_backtest_analysis.py](../../raw/articles/chung-khoan/ch16_10_regime_backtest_analysis.py)
