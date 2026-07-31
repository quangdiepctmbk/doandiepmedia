---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch17_11_dl_portfolio_allocation.py
  - raw/articles/chung-khoan/ch17_12_vlstm_portfolio.py
  - raw/articles/chung-khoan/ch17_13_deepm_regime_robust.py
  - raw/articles/chung-khoan/ch17_deepm/ (10 files)
---

# DL End-to-End Portfolio Allocation

Bypass the predict-then-optimize pipeline: neural network that directly maximizes portfolio objective.

## Three Approaches (Ch17)

- **DL Portfolio** (NB11, Zhang-Zohren-Roberts 2020): NN → Sharpe ratio loss, fully end-to-end
- **VLSTM** (NB12, Saly-Kaufmann): variable-selection network + LSTM + pooled-Sharpe loss, volatility-targeted long-short
- **DeePM** (NB13, Wood-Roberts-Zohren 2026): regime-robust end-to-end policy. SoftMin objective penalizes poor performance in any rolling window. deepm/ module includes: configs, dataset, features, graph, losses, model, train, inference, utils.

## Trade-offs

- Higher estimation burden vs two-step pipeline
- Risk of overfitting to in-sample regimes
- Need extensive walk-forward validation
- Interpretability harder

## Links

- [[portfolio-construction-ml]]
- [[mvo-robust-kelly]]
- [[hierarchical-risk-parity]]
- [[conformal-position-sizing]]
- [[allocator-comparison-protocol]]
- [[dl-time-series-forecasting]]

## Sources

- [ch17_11_dl_portfolio_allocation.py](../../raw/articles/chung-khoan/ch17_11_dl_portfolio_allocation.py)
- [ch17_12_vlstm_portfolio.py](../../raw/articles/chung-khoan/ch17_12_vlstm_portfolio.py)
- [ch17_13_deepm_regime_robust.py](../../raw/articles/chung-khoan/ch17_13_deepm_regime_robust.py)
