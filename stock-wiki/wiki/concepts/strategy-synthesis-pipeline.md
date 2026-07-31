---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch20_README.md]
---

# Strategy Synthesis (ML4T Ch20)

The final chapter passes 9 case studies through a standardized pipeline. The unit of comparison is each case study's arc from signal to frozen holdout.

## Pipeline Stages

1. **Holdout Predictions**: frozen out-of-sample validation (NB00, holdout.py)
2. **Feature Evaluation**: FDR-controlled triage — feature survival ≠ strategy survival (NB02)
3. **Signal Quality**: IC + ICIR + positive-fold share + checkpoint sensitivity (NB03)
4. **Signal → Strategy**: Fundamental Law mapping; family ranking shifts (NB04)
5. **Portfolio Allocation**: allocator winners by case study (NB05)
6. **Cost Survival**: breakeven scorecard; options HTM cascade (NB06)
7. **Regime Risk**: 3 decay mechanisms — prediction, translation, structural break (NB07)
8. **Causal Credibility**: DML estimates as fragility metric (NB08)
9. **Recommendations**: per-CS next-step ledger; ensemble opportunity (NB08)

## Key Framing

- Feature triage is a screen, not a strategy-survival predictor
- IC → Sharpe gap is real and pervasive
- Cost survival is the gate; breakeven determines deployability
- Three distinct holdout decay mechanisms

## Links

- [[feature-triage-evaluation]]
- [[signal-quality-bundle]]
- [[signal-to-strategy-translation]]
- [[cost-survival-breakeven]]
- [[regime-risk-decay]]
- [[causal-credibility-fragility]]
- [[strategy-recommendation-pipeline]]
- [[holdout-validation-framework]]
- [[ml-backtest-baseline]]
- [[evidence-boundary]]

## Sources

- [ch20_README.md](../../raw/articles/chung-khoan/ch20_README.md)
- [[ch20-strategy-synthesis]]
