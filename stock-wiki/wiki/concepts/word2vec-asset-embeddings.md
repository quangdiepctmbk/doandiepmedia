---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch10_01_word2vec_training.py
  - raw/articles/chung-khoan/ch10_02_asset_embeddings.py
---

# Word2Vec Asset Embeddings

Asset embeddings apply the Word2Vec skip-gram idea to institutional portfolio holdings: stocks are treated like words, portfolios like sentences, and portfolio position order like word order.

## Mapping

| NLP | Finance |
|-----|---------|
| Sentence | Portfolio (stocks ordered by holding size) |
| Word | Stock / CUSIP |
| Context window | Nearby portfolio positions |
| Similar meaning | Similar investment characteristics |

## Core Insight

If stocks frequently appear in similar positions across many institutional portfolios, investors are treating them as economically similar. Word2Vec can learn this from 13F holdings without hand-designed fundamental labels.

## Notebook Implementation

`02_asset_embeddings.py` uses 2024Q3 13F bulk holdings, top 500 institutions, `vector_size=100`, `window=5`, `min_count=5`, skip-gram. Validated via masked asset prediction benchmark (Gabaix et al. 2025 NBER WP 33651).

## Links

- [[financial-nlp-representations]]
- [[text-feature-engineering]]
- [[panel-temporal-features]]

## Sources

- [ch10_01_word2vec_training.py](../../raw/articles/chung-khoan/ch10_01_word2vec_training.py)
- [ch10_02_asset_embeddings.py](../../raw/articles/chung-khoan/ch10_02_asset_embeddings.py)
- [[ch10-text-feature-engineering]]
