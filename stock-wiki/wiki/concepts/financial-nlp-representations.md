---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch10_README.md
  - raw/articles/chung-khoan/ch10_01_word2vec_training.py
  - raw/articles/chung-khoan/ch10_03_sentiment_evolution.py
---

# Financial NLP Representations

Financial NLP representations cover the evolution from count-based methods (TF-IDF, lexicons) to static embeddings (Word2Vec, GloVe) to contextual Transformer embeddings, and their role in financial text features.

## 1. Lexical / Statistical

Bag-of-words and TF-IDF are fast, interpretable, and domain-adaptable. They remain useful baselines but lose: word order, negation, synonymy, polysemy, and long-range context.

## 2. Static Embeddings

Word2Vec and GloVe learn dense semantic representations from co-occurrence. The distributional hypothesis: words appearing in similar contexts have similar vector representations. Limitation: one vector per word regardless of context.

## 3. Contextual Embeddings

Transformers generate context-specific token/document embeddings via self-attention. This addresses polysemy and long-range dependence and is the modern default for financial text classification and feature extraction.

## Links

- [[word2vec-asset-embeddings]]
- [[transformers-for-financial-text]]
- [[text-feature-engineering]]

## Sources

- [ch10_README.md](../../raw/articles/chung-khoan/ch10_README.md)
- [ch10_01_word2vec_training.py](../../raw/articles/chung-khoan/ch10_01_word2vec_training.py)
- [ch10_03_sentiment_evolution.py](../../raw/articles/chung-khoan/ch10_03_sentiment_evolution.py)
