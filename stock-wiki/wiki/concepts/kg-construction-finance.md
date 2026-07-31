---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch23_01_sp100_sec_download.py
  - raw/articles/chung-khoan/ch23_02_supply_chain_kg_construction.py
  - raw/articles/chung-khoan/ch23_05_institutional_holdings_kg.py
  - raw/articles/chung-khoan/ch23_08_8k_event_extraction.py
---

# Financial KG Construction

Building financial KGs is primarily a governance problem: identity resolution, schema discipline, provenance, and temporal consistency.

## Construction Notebooks

- **NB01 S&P 100 SEC filings** — load/inspect 10-K and 8-K filings, verify coverage and text quality
- **NB02 Supply Chain KG** — extract supplier/customer/competitor relationships from 10-K filings using Qwen2.5-7B, resolve entities, load triples to Neo4j
- **NB05 Institutional Holdings KG** — build 13F property graph; shared-holding/crowding queries; Jaccard co-ownership
- **NB08 8-K Event Extraction** — structured event quadruples with FinReflectKG critic-corrector reflection loop

## Key Requirements

- Entity deduplication and stable IDs
- Typed relationships with finite vocabulary
- Edge provenance: source filing, date, extractor/model, confidence
- Replayable extraction pipeline

## Links

- [[financial-knowledge-graphs]]
- [[graph-rag-finance]]
- [[temporal-kg-leakage]]
- [[rag-applications-finance]]

## Sources

- [ch23_01_sp100_sec_download.py](../../raw/articles/chung-khoan/ch23_01_sp100_sec_download.py)
- [ch23_02_supply_chain_kg_construction.py](../../raw/articles/chung-khoan/ch23_02_supply_chain_kg_construction.py)
- [ch23_05_institutional_holdings_kg.py](../../raw/articles/chung-khoan/ch23_05_institutional_holdings_kg.py)
- [ch23_08_8k_event_extraction.py](../../raw/articles/chung-khoan/ch23_08_8k_event_extraction.py)
