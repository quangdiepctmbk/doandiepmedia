---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch15_03_econml_dml.py
  - raw/articles/chung-khoan/ch15_04_dml_crypto_regime.py
  - raw/articles/chung-khoan/ch15_05_momentum_causal_trading.py
---

# Double Machine Learning (DML)

Double Machine Learning estimates causal effects of continuous treatments in the presence of high-dimensional confounders via orthogonalization and cross-fitting.

## How It Works

1. **Nuisance models**: fit ML models for E[treatment|confounders] and E[outcome|confounders]
2. **Orthogonalization**: compute residuals (treatment - predicted treatment, outcome - predicted outcome)
3. **Causal estimate**: regress outcome residuals on treatment residuals
4. **Cross-fitting**: split data, fit nuisances on one fold, estimate on the other (avoid overfitting bias)

## Ch15 Applications

- **NB03**: skip-recent 6-1 momentum → 21-day ETF returns. HAC SE inflation, walk-forward cross-fitting, block-permutation refutation
- **NB04**: crypto premium z-score → 8h returns, subgroup by volatility regime
- **NB05**: CausalForestDML for regime-conditional CATEs → position sizing vs transaction costs
- **NB10**: cross-case-study DML synthesis — confounding bias pervasive

## Links

- [[causal-ml-trading]]
- [[causal-validation-refutation]]
- [[causal-case-study-insights]]
- [[walk-forward-evaluation]]

## Sources

- [ch15_03_econml_dml.py](../../raw/articles/chung-khoan/ch15_03_econml_dml.py)
- [ch15_04_dml_crypto_regime.py](../../raw/articles/chung-khoan/ch15_04_dml_crypto_regime.py)
- [ch15_05_momentum_causal_trading.py](../../raw/articles/chung-khoan/ch15_05_momentum_causal_trading.py)
