---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch16_11_sharpe_ratio_inference.py
  - raw/articles/chung-khoan/ch16_12_dsr_validation.py
  - raw/articles/chung-khoan/ch16_13_ras_protocol.py
---

# Search-Aware Sharpe Inference

A reported Sharpe ratio must account for three layers of uncertainty:

1. **Estimation error** (Lo 2002): fixed-strategy confidence intervals
2. **Selection bias** (Bailey-Lopez de Prado 2014): DSR corrects for searching across N strategies
3. **Reality Check** (White 2000): bootstrap-based test if the best model beats benchmark

## Tools

- **DSR** (NB12): Deflated Sharpe Ratio — accounts for number of trials, return distribution skew/kurtosis
- **RAS Protocol** (NB13): Rademacher Anti-Serum — bounds strategy set complexity for tighter inference
- Bootstrap: simulate selection in repeated samples

NB11 covers proper Sharpe ratio inference (confidence intervals, autocorrelation adjustment).

## Links

- [[strategy-simulation-backtesting]]
- [[performance-reporting-framework]]
- [[multiple-testing-selection-bias]]
- [[ml-backtest-baseline]]

## Sources

- [ch16_11_sharpe_ratio_inference.py](../../raw/articles/chung-khoan/ch16_11_sharpe_ratio_inference.py)
- [ch16_12_dsr_validation.py](../../raw/articles/chung-khoan/ch16_12_dsr_validation.py)
- [ch16_13_ras_protocol.py](../../raw/articles/chung-khoan/ch16_13_ras_protocol.py)
