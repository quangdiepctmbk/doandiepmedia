---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch19_08_ml_exit_signals.py
  - raw/articles/chung-khoan/ch19_09_deep_hedging.py
---

# ML Exit Signals & Deep Hedging

ML-based risk controls that go beyond rule-based stops.

## ML Exit Signals (NB08)

Two-model architecture:
- Entry model: predicts high-return opportunities
- Exit model: predicts adverse moves
- Separate models for separate purposes → cleaner signal

## Deep Hedging (NB09, Buehler et al. 2019)

Neural network learns hedging positions minimizing CVaR of terminal PnL under transaction costs. Bridges gap between risk measurement (VaR/CVaR) and learned control. End-to-end optimization under realistic costs.

## Links

- [[risk-management-ml]]
- [[stress-testing-drift]]
- [[var-cvar-path-risk]]
- [[deep-hedging]]
- [[dl-portfolio-allocation]]

## Sources

- [ch19_08_ml_exit_signals.py](../../raw/articles/chung-khoan/ch19_08_ml_exit_signals.py)
- [ch19_09_deep_hedging.py](../../raw/articles/chung-khoan/ch19_09_deep_hedging.py)
