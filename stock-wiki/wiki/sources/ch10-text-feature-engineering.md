---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch10_README.md
ingested: 2026-07-26
related_raw:
  - ch10_01_word2vec_training.py
  - ch10_02_asset_embeddings.py
  - ch10_03_sentiment_evolution.py
  - ch10_04_bert_finetuning.py
  - ch10_05_financial_ner_finetuning.py
  - ch10_06_finbert_cross_dataset.py
  - ch10_07_news_return_signals.py
  - ch10_08_text_feature_evaluation.py
  - ch10_09_filing_text_signals.py
---

# Text Feature Engineering — Chương 10 (ML4T)

## Summary

Chương này covers systematic NLP pipeline cho trading: từ lexical baselines (TF-IDF, lexicons) qua static embeddings (Word2Vec, GloVe) đến Transformer-based models (BERT, FinBERT, ModernBERT), và kết thúc bằng practical workflow xây dựng alpha factors từ text signals.

9 notebooks chia làm 5 sections:

1. **10.1 Lexical & Statistical Models** — Bag-of-words, TF-IDF, financial lexicons (Loughran-McDonald). Fast, interpretable, không capture context/polysemy.
2. **10.2 Static Embeddings** — Word2Vec (skip-gram/CBOW), GloVe. Một vector/từ — không xử lý được polysemy.
3. **10.3 Sequential Models** — RNN, LSTM. Bridge giữa static embeddings và Transformers.
4. **10.4 Transformers** — Self-attention, multi-head attention, positional encoding, BERT, FinBERT, ModernBERT. Contextual embeddings giải quyết polysemy.
5. **10.5 Modern Feature Extraction Workflow** — Point-in-time alignment, entity resolution, model cutoff dates, signal aggregation rules, evaluation protocols.

## Notebooks & Case Studies

| Notebook | Content | Docker Image |
|----------|---------|-------------|
| 01_word2vec_training | Skip-gram/CBOW trên Financial PhraseBank | ml4t-py312 |
| 02_asset_embeddings | Word2Vec trên 13F portfolios (Gabaix et al. 2025) | ml4t-py312 |
| 03_sentiment_evolution | TF-IDF → GloVe → FinBERT benchmark trên PhraseBank | ml4t-py312 |
| 04_bert_finetuning | Fine-tune FinBERT vs DeBERTa-v3 vs ModernBERT | ml4t-gpu |
| 05_financial_ner_finetuning | Fine-tune FinBERT cho NER (ORG, MONEY, DATE, PER, PERCENT) | ml4t-gpu |
| 06_finbert_cross_dataset | Distribution shift: FinBERT PhraseBank → FinMarBa headlines | ml4t-gpu |
| 07_news_return_signals | News surprise factor từ FNSPID 15.7M articles | ml4t-gpu |
| 08_text_feature_evaluation | IC, ICIR, quintile spread cho text signals | ml4t |
| 09_filing_text_signals | SEC 10-Q MD&A → FinBERT sentiment + narrative change signals | ml4t-gpu |

## Key Takeaways

- **TF-IDF vẫn hữu ích**: trên noisy dataset (mixed-agreement) TF-IDF outperforms FinBERT vì distribution shift (NB06)
- **Transformers cần fine-tuning**: FinBERT pre-trained (no fine-tune) thua TF-IDF khi distribution shift, nhưng sau fine-tuning outperform mọi baselines
- **Asset Embeddings** (Gabaix et al. 2025): Word2Vec trên portfolio holdings → stock embeddings capture investment characteristics, validated via masked-asset prediction benchmark
- **News Surprise**: semantic deviation from recent narrative patterns → abnormal returns (Bhargava et al. 2023)
- **SEC Filing Signals**: FinBERT sentiment + sentence-transformer narrative change từ MD&A → both positive alpha factors
- **Point-in-time là mandatory**: every text-derived signal cần timestamp đúng, model cutoff dates, và aggregation rules rõ ràng

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 10
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/10_text_feature_engineering)
- [[ch09-model-based-features]] (previous chapter)
