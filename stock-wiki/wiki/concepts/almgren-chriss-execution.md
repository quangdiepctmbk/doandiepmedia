---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch18_04_vwap_twap_execution.py
  - raw/articles/chung-khoan/ch18_05_almgren_chriss_optimal_execution.py
  - raw/articles/chung-khoan/ch18_06_ml4t_execution_demo.py
  - raw/articles/chung-khoan/ch18_07_ml4t_volume_participation.py
  - raw/articles/chung-khoan/ch18_08_ml_dynamic_execution.py
---

# Execution Algorithms & Almgren-Chriss

Execution algorithms manage the trade-off between market impact, timing risk, and signal decay.

## Execution Toolbox

- **TWAP/VWAP** (NB04): time-weighted / volume-weighted benchmarks
- **Volume Participation** (NB07): ml4t.backtest.execution VolumeParticipationLimit
- **ML Dynamic Execution** (NB08): RL/ML adapts parameters to real-time conditions
- **ML4T Library** (NB06): 4 market impact models in ml4t.backtest.execution

## Almgren-Chriss (NB05)

Cleanest framework: efficient frontier of execution strategies.

- Impact = permanent + temporary components
- Timing risk = price volatility during execution
- Urgency = signal half-life determines optimal speed
- Analytical optimal trajectory = `x(t) = sinh(κ(T−t)) / sinh(κT)`

## Links

- [[transaction-costs-ml]]
- [[cost-taxonomy-asset-class]]
- [[market-impact-calibration]]
- [[ml-dynamic-execution]]
- [[cost-model-benchmark]]

## Sources

- [ch18_04_vwap_twap_execution.py](../../raw/articles/chung-khoan/ch18_04_vwap_twap_execution.py)
- [ch18_05_almgren_chriss_optimal_execution.py](../../raw/articles/chung-khoan/ch18_05_almgren_chriss_optimal_execution.py)
- [ch18_06_ml4t_execution_demo.py](../../raw/articles/chung-khoan/ch18_06_ml4t_execution_demo.py)
- [ch18_07_ml4t_volume_participation.py](../../raw/articles/chung-khoan/ch18_07_ml4t_volume_participation.py)
- [ch18_08_ml_dynamic_execution.py](../../raw/articles/chung-khoan/ch18_08_ml_dynamic_execution.py)
