---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch10_03_sentiment_evolution.py
  - raw/articles/chung-khoan/ch10_06_finbert_cross_dataset.py
---

# FinBERT Distribution Shift

The gap between a financial sentiment model's performance on its training distribution and its performance on a different financial text distribution with apparently similar labels.

## Key Lesson

Same labels do not imply same distribution. Financial PhraseBank (curated news sentences, human annotation) and FinMarBa (headlines labeled by market reactions) differ in source, style, and labeling basis.

## Practical Implication

A pre-trained financial sentiment model should not be treated as plug-and-play alpha. Before using its output as a trading feature:

1. test on target-domain text
2. inspect confusion matrix by class
3. compare against TF-IDF baseline
4. evaluate predictive IC after timestamp alignment
5. fine-tune if the target distribution differs materially

## Links

- [[transformers-for-financial-text]]
- [[text-feature-signal-evaluation]]
- [[news-text-alpha-signals]]
- [[multiple-testing-selection-bias]]

## Sources

- [ch10_03_sentiment_evolution.py](../../raw/articles/chung-khoan/ch10_03_sentiment_evolution.py)
- [ch10_06_finbert_cross_dataset.py](../../raw/articles/chung-khoan/ch10_06_finbert_cross_dataset.py)
