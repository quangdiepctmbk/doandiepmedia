---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch20_00_holdout_predictions.py
  - raw/articles/chung-khoan/ch20_holdout.py
  - raw/articles/chung-khoan/ch20_02_feature_evaluation.py
  - raw/articles/chung-khoan/ch20_03_signal_quality.py
---

# Signal Quality & Feature Evaluation

Cross-case-study analysis of feature triage and signal quality.

## Feature Evaluation (NB02)

- FDR-controlled triage funnel (Table 20.3)
- Feature survival ≠ strategy survival — triage là screen, không phải predictor
- Cross-case-study survival patterns

## Signal Quality Bundle (NB03)

- IC + ICIR + positive-fold share + checkpoint sensitivity
- Per-CS family-mean IC table (Table 20.4)
- IC vs Sharpe scatter (Figure 20.2) — IC → Sharpe gap pervasive
- Label engineering impact on signal quality

## Links

- [[strategy-synthesis-pipeline]]
- [[signal-to-strategy-translation]]
- [[information-coefficient]]
- [[feature-selection-dedup]]
- [[feature-design-grammar]]

## Sources

- [ch20_00_holdout_predictions.py](../../raw/articles/chung-khoan/ch20_00_holdout_predictions.py)
- [ch20_holdout.py](../../raw/articles/chung-khoan/ch20_holdout.py)
- [ch20_02_feature_evaluation.py](../../raw/articles/chung-khoan/ch20_02_feature_evaluation.py)
- [ch20_03_signal_quality.py](../../raw/articles/chung-khoan/ch20_03_signal_quality.py)
