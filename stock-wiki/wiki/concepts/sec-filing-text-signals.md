---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch10_09_filing_text_signals.py]
---

# SEC Filing Text Signals

SEC filing text signals convert 10-Q MD&A text into alpha factors using sentiment and semantic-change features.

## Notebook 09 Workflow

`09_filing_text_signals.py` uses S&P 500 10-Q MD&A sections (2017-2021), anchored by SEC acceptance date (not quarter-end).

Two complementary signal types:

1. **FinBERT sentiment** — directional bias in management language
2. **Narrative change** — quarter-over-quarter semantic shift via sentence-transformer embeddings, measuring how much management's story has shifted

## Point-in-Time Anchor

The tradable timestamp is the SEC filing date. A signal becomes available when the filing is accepted, not when the fiscal quarter ends. Same-date multi-quarter filings are collapsed to the latest period_end.

## Coverage

- Default run: 50 symbols, ~750 filings
- Full: 477 companies, 6,770 filings
- Evaluated via IC, ICIR, and quintile analysis

## Links

- [[text-feature-engineering]]
- [[text-feature-signal-evaluation]]
- [[transformers-for-financial-text]]
- [[slow-moving-contextual-features]]
- [[information-coefficient]]

## Sources

- [ch10_09_filing_text_signals.py](../../raw/articles/chung-khoan/ch10_09_filing_text_signals.py)
- [[ch10-text-feature-engineering]]
