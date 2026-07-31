---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch10_README.md
  - raw/articles/chung-khoan/ch10_04_bert_finetuning.py
  - raw/articles/chung-khoan/ch10_06_finbert_cross_dataset.py
---

# Transformers for Financial Text

Transformers are the modern architecture for financial text representation because self-attention creates context-dependent embeddings that handle polysemy, negation, and long-range dependence better than TF-IDF or static embeddings.

## Core Components

- **Self-attention**: each token attends to other tokens in the sequence
- **Multi-head attention**: multiple relation types captured in parallel
- **Positional encoding**: injects order information
- **BERT-style encoders**: strong for classification/extraction tasks
- **Finance checkpoints**: FinBERT, ModernBERT-style general checkpoints fine-tuned on finance tasks

## Fine-Tuning Workflow

`04_bert_finetuning.py` fine-tunes and compares `ProsusAI/finbert`, `microsoft/deberta-v3-small`, and `answerdotai/ModernBERT-base` using Hugging Face Trainer, validation split, early stopping, accuracy/F1, and confusion matrices.

## Distribution Shift Warning

`06_finbert_cross_dataset.py` shows same-label does not mean same-distribution. FinBERT trained on Financial PhraseBank is evaluated on FinMarBa market-reaction headlines; performance gaps reveal domain/text-source shift.

## Links

- [[financial-nlp-representations]]
- [[finbert-distribution-shift]]
- [[financial-ner-extraction]]
- [[text-feature-engineering]]

## Sources

- [ch10_README.md](../../raw/articles/chung-khoan/ch10_README.md)
- [ch10_04_bert_finetuning.py](../../raw/articles/chung-khoan/ch10_04_bert_finetuning.py)
- [ch10_06_finbert_cross_dataset.py](../../raw/articles/chung-khoan/ch10_06_finbert_cross_dataset.py)
