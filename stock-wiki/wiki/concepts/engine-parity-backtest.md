---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch16_06_framework_parity.py
  - raw/articles/chung-khoan/ch16_07_engine_divergence_anatomy.py
  - raw/articles/chung-khoan/ch16_15_lean_engine_parity.py
  - raw/articles/chung-khoan/ch16_16_case_study_lean_parity.py
  - raw/articles/chung-khoan/ch16_17_backtrader_zipline_engine_parity.py
  - raw/articles/chung-khoan/ch16_18_vectorbt_engine_parity.py
---

# Engine Parity in Backtesting

Same strategy, different engines → different results. Engine parity testing reveals how protocol assumptions (fill timing, cash release, dividend treatment) drive divergence.

## Parity Tests (Ch16)

- NB06: ETF momentum protocol parity across frameworks
- NB07: anatomy of engine divergence (where differences come from)
- NB15: ml4t-backtest vs LEAN (QuantConnect) engine
- NB16: case-study LEAN parity (real book artifacts)
- NB17: Backtrader + Zipline Reloaded parity
- NB18: VectorBT OSS parity

## Key Insight

Different engines produce different equity curves for the same strategy — understanding the source of divergence is critical before claiming "alpha".

## Links

- [[strategy-simulation-backtesting]]
- [[vectorized-vs-event-driven]]
- [[backtest-trading-protocol]]
- [[performance-reporting-framework]]

## Sources

- [ch16_06_framework_parity.py](../../raw/articles/chung-khoan/ch16_06_framework_parity.py)
- [ch16_07_engine_divergence_anatomy.py](../../raw/articles/chung-khoan/ch16_07_engine_divergence_anatomy.py)
- [ch16_15_lean_engine_parity.py](../../raw/articles/chung-khoan/ch16_15_lean_engine_parity.py)
- [ch16_16_case_study_lean_parity.py](../../raw/articles/chung-khoan/ch16_16_case_study_lean_parity.py)
- [ch16_17_backtrader_zipline_engine_parity.py](../../raw/articles/chung-khoan/ch16_17_backtrader_zipline_engine_parity.py)
- [ch16_18_vectorbt_engine_parity.py](../../raw/articles/chung-khoan/ch16_18_vectorbt_engine_parity.py)
