---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch10_05_financial_ner_finetuning.py]
---

# Financial NER Extraction

Financial named entity recognition (NER) extracts structured entities (companies, amounts, dates) from unstructured financial text, enabling automated information extraction from earnings calls, SEC filings, and news.

## Entity Types in Ch10

`05_financial_ner_finetuning.py` fine-tunes FinBERT for token classification using IOB2 tags:

- `ORG` — organization/company
- `MONEY` — monetary amount
- `DATE` — date/time expression
- `PER` — person
- `PERCENT` — percentage

## Why It Matters

NER enables downstream structured features: company mention counts, event/entity co-occurrence, extracted monetary guidance, timeline construction, and knowledge graph edges.

## Links

- [[transformers-for-financial-text]]
- [[text-feature-engineering]]
- [[sec-filing-text-signals]]
- [[slow-moving-contextual-features]]

## Sources

- [ch10_05_financial_ner_finetuning.py](../../raw/articles/chung-khoan/ch10_05_financial_ner_finetuning.py)
- [[ch10-text-feature-engineering]]
