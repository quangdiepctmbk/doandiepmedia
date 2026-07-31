---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_03_logistic_classification.py
---

# Logistic Classification for Trading

Logistic regression predicts return direction (up/down) rather than magnitude. Direction prediction is often more tractable than continuous return prediction because most trading decisions reduce to long/short/flat.

## Trade-offs vs Regression

- Classification is natural when decisions are directional (binary positions)
- Probabilities can be scaled to position sizes (confidence → allocation)
- Calibration matters: poorly calibrated probabilities produce wrong position sizes
- Class imbalance (more up days than down days) needs handling

## NB03

Uses same ETF features and walk-forward folds as NB02, predicting 21-day forward direction. Evaluated via accuracy, precision/recall, and backtest returns.

## Links

- [[regularized-regression-trading]]
- [[ml-pipeline-trading]]
- [[walk-forward-evaluation]]
- [[learning-task-definition]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_03_logistic_classification.py](../../raw/articles/chung-khoan/ch11_03_logistic_classification.py)
