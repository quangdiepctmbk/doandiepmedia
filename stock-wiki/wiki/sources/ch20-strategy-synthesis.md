---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch20_README.md
ingested: 2026-07-26
related_raw:
  - ch20_holdout.py
  - ch20_00_holdout_predictions.py
  - ch20_01_aggregate_synthesis.py
  - ch20_02_feature_evaluation.py
  - ch20_03_signal_quality.py
  - ch20_04_signal_to_strategy.py
  - ch20_05_portfolio_allocation.py
  - ch20_06_cost_survival.py
  - ch20_07_regime_risk.py
  - ch20_08_recommendations.py
---

# Strategy Synthesis — Chương 20 (ML4T)

## Summary

Chương 20 là synthesis cuối cùng: pass 9 case studies through cùng một standardized pipeline (data → features → labels → models → predictions → portfolios → costs → risk overlays). Unit of comparison: arc từ signal đến frozen holdout, không phải league-table Sharpe ranking.

9 sections, 9 notebooks + holdout.py utility.

### Sections & Notebooks:

1. **20.1 Nine Case Studies End-to-End**: per-CS arc signal → portfolio → holdout; rank-1 cluster reading
2. **20.2 Feature Evaluation**: FDR-controlled triage funnel; feature survival ≠ strategy survival (NB02)
3. **20.3 Signal Quality**: IC + ICIR + positive-fold share + checkpoint sensitivity (NB03)
4. **20.4 Signal → Strategy**: Fundamental Law mapping; family rankings shift across pipeline (NB04)
5. **20.5 Portfolio Allocation**: HRP wins where signal is broad; spread widens when signal weak (NB05)
6. **20.6 Cost Survival**: per-CS breakeven against cost; SP500 options HTM cascade (NB06)
7. **20.7 Regime Risk**: 3 decay mechanisms — prediction, translation, regime; overlay effectiveness (NB07)
8. **20.8 Causal Credibility**: DML as fragility metric; publication-standard + refutation (NB08)
9. **20.9 Limitations & Workflow**: constraint inventory; ensemble opportunity; per-CS next steps

### Key Takeaways

- **Feature survival ≠ strategy survival**: feature triage là screen, không phải predictor
- **IC → Sharpe gap**: strong IC không đảm bảo strategy deployment
- **Allocator wins context-dependent**: HRP mạnh khi signal broad; spread lớn khi signal weak
- **Cost survival là gate**: breakeven scorecard quyết định strategy viability
- **3 decay mechanisms**: prediction quality drift, portfolio translation drift, structural break
- **DML estimates** as fragility metric cho causal claims

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 20
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/20_strategy_synthesis)
- [[ch19-risk-management]] (previous chapter)
