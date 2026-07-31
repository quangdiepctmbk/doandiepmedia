---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch20_07_regime_risk.py
  - raw/articles/chung-khoan/ch20_08_recommendations.py
---

# Regime Risk Decay & Strategy Recommendations

Three distinct mechanisms cause validation → holdout decay. Synthesis of cross-case-study evidence.

## Three Decay Mechanisms (NB07)

1. **Prediction quality drift**: model degrades on holdout data
2. **Portfolio translation drift**: same predictions → different portfolio outcomes
3. **Structural break**: regime change invalidates the X→y relationship

Risk overlay effectiveness is strategy-specific (Figure 20.7).

## Causal Credibility (NB08)

- DML estimates as fragility metric
- Publication-standard threshold + refutation companion

## Recommendations (NB08)

- Pipeline evidence snapshot (Table 20.11)
- Per-CS next-step ledger
- Ensembling note: ensemble opportunity identified across case studies
- Constraint inventory for next iteration

## Links

- [[strategy-synthesis-pipeline]]
- [[signal-quality-feature-triage]]
- [[signal-to-cost-survival]]
- [[causal-ml-trading]]
- [[causal-case-study-insights]]
- [[evidence-boundary]]

## Sources

- [ch20_07_regime_risk.py](../../raw/articles/chung-khoan/ch20_07_regime_risk.py)
- [ch20_08_recommendations.py](../../raw/articles/chung-khoan/ch20_08_recommendations.py)
