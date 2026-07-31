---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch16_README.md
ingested: 2026-07-26
related_raw:
  - ch16_01_backtest_first_principles.py
  - ch16_02_futures_backtesting.py
  - ch16_03_single_asset_vectorbt.py
  - ch16_04_single_asset_ml4t_backtest.py
  - ch16_05_stateful_strategies.py
  - ch16_06_framework_parity.py
  - ch16_07_engine_divergence_anatomy.py
  - ch16_08_signal_method_comparison.py
  - ch16_09_performance_reporting.py
  - ch16_10_regime_backtest_analysis.py
  - ch16_11_sharpe_ratio_inference.py
  - ch16_12_dsr_validation.py
  - ch16_13_ras_protocol.py
  - ch16_14_cost_sensitivity.py
  - ch16_15_lean_engine_parity.py
  - ch16_16_case_study_lean_parity.py
  - ch16_17_backtrader_zipline_engine_parity.py
  - ch16_18_vectorbt_engine_parity.py
  - ch16__etf_baseline.py
---

# Strategy Simulation — Chương 16 (ML4T)

## Summary

Chương 16 định nghĩa **backtesting như một falsification discipline**: backtest không phải để chứng minh strategy hoạt động, mà để chứng minh nó **fail** dưới assumptions thực tế. Từ vectorized vs event-driven, non-ML baseline, performance reporting, regime diagnostics, đến Sharpe ratio inference và search-aware validation (DSR).

18 notebooks + _etf_baseline.py utility chia làm 8 sections:

1. **16.1-2 Backtesting as Falsification / Trading Protocol** — protocol specification: timing, rebalancing, sizing, fills, costs, constraints
2. **16.3 Vectorized vs Event-Driven** — simulation semantics, cash release, order sequencing
3. **16.4 Building Baseline** — transparent non-ML ETF strategy làm benchmark cho ML results
4. **16.5 Performance Reporting** — return, risk, risk-adjusted, turnover, cost-impact metrics
5. **16.6 Regime Diagnostics** — slice results across volatility/trend states
6. **16.7 Strategy-Level Overfitting** — DSR, Reality Check, RAS protocol
7. **16.8 Summary** — falsification discipline, Ch17-19 setup

## Key Takeaways

- Backtest là falsification, không phải performance worship
- Vectorized ≠ Event-driven: semantics khác nhau, không phải cái nào "tốt hơn"
- **Baseline là bắt buộc**: non-ML strategy phải được define trước khi so ML
- **Gross vs Net, Sharpe uncertainty, turnover, baseline comparison**: tất cả trong cùng report
- **Regime-sliced**: aggregate stats có thể bị driven bởi favorable environments
- **Prediction quality ≠ trading quality**: IC không đủ để chọn strategy deployable
- DSR (Deflated Sharpe Ratio) và RAS protocol để correct cho search-aware inference

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 16
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/16_strategy_simulation)
- [[ch15-causal-estimation]] (previous chapter)
