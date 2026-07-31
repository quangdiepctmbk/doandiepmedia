---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch10_08_text_feature_evaluation.py]
---

# Text Feature Signal Evaluation

Applies standard factor diagnostics to NLP-derived alpha signals, focusing on whether the signal predicts forward returns rather than whether the NLP benchmark score is high.

## Diagnostics

`08_text_feature_evaluation.py` computes for each text signal:

- daily cross-sectional Spearman IC
- ICIR and t-statistics
- quintile portfolio spreads
- long-short Q5-Q1 analysis
- coverage-aware diagnostics (min assets per day)

## Core Principle

NLP accuracy is not alpha. A text model only matters for trading if its time-aligned features show stable predictive relationship to forward returns.

## Links

- [[news-text-alpha-signals]]
- [[information-coefficient]]
- [[ic-inference]]
- [[multiple-testing-selection-bias]]
- [[walk-forward-evaluation]]

## Sources

- [ch10_08_text_feature_evaluation.py](../../raw/articles/chung-khoan/ch10_08_text_feature_evaluation.py)
- [[ch10-text-feature-engineering]]
