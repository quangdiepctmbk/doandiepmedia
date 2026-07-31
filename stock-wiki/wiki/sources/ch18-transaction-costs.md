---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch18_README.md
ingested: 2026-07-26
related_raw:
  - ch18_01_cost_taxonomy.py
  - ch18_02_spread_estimation.py
  - ch18_03_market_impact_calibration.py
  - ch18_04_vwap_twap_execution.py
  - ch18_05_almgren_chriss_optimal_execution.py
  - ch18_06_ml4t_execution_demo.py
  - ch18_07_ml4t_volume_participation.py
  - ch18_08_ml_dynamic_execution.py
  - ch18_09_frequency_tradeoff.py
  - ch18_10_gross_vs_net_performance.py
  - ch18_11_cost_cliff.py
  - ch18_12_commission_slippage_comparison.py
  - ch18__cost_analysis.py
---

# Transaction Costs — Chương 18 (ML4T)

## Summary

Chương 18 reframes transaction costs từ backtest adjustment thành **workflow constraint**: ảnh hưởng đến factor evaluation, simulation, portfolio construction, risk management, production monitoring. Central claim: many strategies fail not because the forecast is wrong, but because the implementation problem was ignored.

12 notebooks + _cost_analysis.py utility + README.

### Sections (8):

1. **18.1 Where Costs Enter**: costs affect every step of ML4T workflow
2. **18.2 Taxonomy**: explicit (commission, fees), implicit (spread, slippage, market impact), capacity costs
3. **18.3 Microstructure Regime Link**: cost parameters non-stationary — time of day, volatility, stress
4. **18.4 Baseline Cost Models**: spread-only → linear slippage → square-root impact
5. **18.5 Execution Algorithms**: TWAP, VWAP, volume participation, ML dynamic execution
6. **18.6 Optimal Execution**: Almgren-Chriss framework — impact vs timing risk vs urgency
7. **18.7 TCA & Model Validation**: implementation shortfall decomposition, recalibration
8. **18.8 Practical Guardrails**: breakeven turnover, minimum edge, alpha-to-go, capacity, kill criteria

### Key Takeaways

- **Modelling choice matters**: 6 commission models × 5 slippage models → large P&L sensitivity
- **Cost parameters are non-stationary**: regime-aware calibration essential
- **Almgren-Chriss**: cleanest framework for impact × timing × urgency
- **Gross → Net gap**: ultimate reality check
- **Cost cliff**: intraday strategies often die after costs
- **TCA closes the loop**: cost assumptions are hypotheses to test, not static inputs

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 18
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/18_transaction_costs)
- [[ch17-portfolio-construction]] (previous chapter)
