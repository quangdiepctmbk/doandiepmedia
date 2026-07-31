---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch19_04_factor_exposure.py
  - raw/articles/chung-khoan/ch19_05_trade_shap_diagnostics.py
---

# Factor Exposure & Trade SHAP Diagnostics

Decompose portfolio risk into factor components; connect ML explanations to trade outcomes.

## Factor Exposure (NB04)

- Regression-based estimation of exposures to market, size, value, profitability, investment factors
- Track exposure changes over time
- Reveal intended vs accidental bets

## Trade SHAP (NB05)

TradeShapAnalyzer from ml4t.diagnostic.evaluation: connects SHAP explanations to trade outcomes. Answers the key risk question: "why did this trade fail?"

## Links

- [[risk-management-ml]]
- [[shap-model-interpretability]]
- [[treeshap-interpretability]]
- [[stress-testing-scenarios]]
- [[drift-detection-monitoring]]

## Sources

- [ch19_04_factor_exposure.py](../../raw/articles/chung-khoan/ch19_04_factor_exposure.py)
- [ch19_05_trade_shap_diagnostics.py](../../raw/articles/chung-khoan/ch19_05_trade_shap_diagnostics.py)
