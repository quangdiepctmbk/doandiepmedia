---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch10_07_news_return_signals.py
  - raw/articles/chung-khoan/ch10_08_text_feature_evaluation.py
---

# News Text Alpha Signals

News text alpha signals convert financial news into stock-date features such as sentiment, narrative surprise, sentiment momentum, and coverage/attention.

## Notebook 07 Workflow

`07_news_return_signals.py` builds factors from FNSPID (15.7M financial news articles, 1999-2023):

1. load news with ticker/date/text
2. compute sentence-transformer embeddings (`all-MiniLM-L6-v2`)
3. score sentiment via `yiyanghkust/finbert-tone`
4. compute **news surprise**: semantic deviation from recent narrative history
5. aggregate by stock and date
6. lag signals by 1 day to avoid look-ahead
7. join to forward returns for evaluation

## News Surprise (Bhargava et al. 2023)

If current news semantics deviate from the stock's recent narrative patterns, that discrepancy predicts abnormal returns.

## Signals

- `weighted_surprise`: news surprise × sentiment direction
- `sentiment_mean`: average daily sentiment
- `sentiment_momentum`: change in sentiment vs baseline
- `coverage_count`: article frequency / attention

## Links

- [[text-feature-signal-evaluation]]
- [[transformers-for-financial-text]]
- [[finbert-distribution-shift]]
- [[information-coefficient]]

## Sources

- [ch10_07_news_return_signals.py](../../raw/articles/chung-khoan/ch10_07_news_return_signals.py)
- [ch10_08_text_feature_evaluation.py](../../raw/articles/chung-khoan/ch10_08_text_feature_evaluation.py)
