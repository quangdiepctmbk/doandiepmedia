---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch10_README.md]
---

# Text Feature Engineering

Text feature engineering là quy trình biến unstructured financial text (news, analyst reports, filings, earnings calls) thành model-ready signals cho systematic trading.

## Feature Families

- **Lexical/statistical**: lexicons, bag-of-words, TF-IDF
- **Static embeddings**: Word2Vec, GloVe — one vector per word/token
- **Contextual embeddings**: BERT/FinBERT/Sentence-BERT — vector depends on surrounding text
- **Structured extraction**: NER, event extraction, topic exposure
- **Alpha signals**: sentiment, narrative surprise, narrative change, coverage/attention

## Production Rule

A strong NLP model is not a tradable feature unless these are point-in-time safe:

1. document timestamp / acceptance timestamp
2. model training cutoff date
3. entity resolution timestamp
4. aggregation window and lag
5. label horizon alignment
6. revision handling

## Links

- [[transformers-for-financial-text]]
- [[news-text-alpha-signals]]
- [[sec-filing-text-signals]]
- [[feature-design-grammar]]
- [[walk-forward-evaluation]]
- [[financial-nlp-representations]]

## Sources

- [ch10_README.md](../../raw/articles/chung-khoan/ch10_README.md)
- [[ch10-text-feature-engineering]]
