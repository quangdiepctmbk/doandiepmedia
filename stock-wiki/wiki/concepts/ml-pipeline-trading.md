---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch11_README.md]
---

# ML Pipeline for Trading

ML pipeline for trading là quy trình từ raw features → model → signal → trade decision, với các bước: preprocessing, model fitting, hyperparameter tuning, interpretability, uncertainty quantification, và backtest validation.

## Core Principle

In trading, unbiased parameter recovery is less important than stable OOS forecasts. This shifts emphasis from inference (p-values, confidence intervals) to prediction (IC, turnover-adjusted returns, calibration).

## Pipeline Stages (Ch11)

- **Linear baselines**: OLS inference → regularized regression (Ridge/LASSO/Elastic Net)
- **Task formulation**: regression vs classification, depends on how forecasts become trades
- **Validation**: walk-forward CV with purging/embargo, nested CV for HPO
- **Interpretability**: SHAP for feature attribution and model debugging
- **Uncertainty**: conformal prediction intervals for risk-aware position sizing
- **Backtest**: IC is not enough — turnover and transaction costs matter

## Links

- [[regularized-regression-trading]]
- [[walk-forward-evaluation]]
- [[shap-model-interpretability]]
- [[conformal-prediction-trading]]
- [[ml-backtest-baseline]]
- [[learning-task-definition]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [[ch11-ml-pipeline]]
