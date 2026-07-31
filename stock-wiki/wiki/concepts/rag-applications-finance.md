---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch22_05_10k_rag_assistant.py
  - raw/articles/chung-khoan/ch22_06_esg_rag_vs_finetune.py
  - raw/articles/chung-khoan/ch22_07_institutional_holdings_graph.py
  - raw/articles/chung-khoan/ch22_08_rag_security.py
---

# RAG Applications: 10-K, ESG, 13F & Security

Practical financial RAG applications.

## 10-K Assistant (NB05)

- Production-grade RAG for SEC 10-K analysis
- Citation-constrained prompting
- Tool-verified numeric computation
- Verifiable citations

## ESG: RAG vs Fine-Tune (NB06)

- **RAG**: evidence-grounded ESG screening — flexible, document-dependent
- **Fine-tune**: classifier for repeatable ESG labels (FinBERT)
- **Decision framework**: RAG for open-ended + changing docs; fine-tune for fixed-label skills

## 13F Holdings Graph (NB07)

- Bipartite institution-stock graph from 13F filings
- Co-ownership similarity, institutional momentum, crowding signals
- Point-in-time features for alpha research

## RAG Security (NB08)

- Untrusted document corpora → adversarial attacks
- Prompt injection, data poisoning, retrieval poisoning
- Defenses: input validation, output filtering, document provenance

## Links

- [[rag-financial-research]]
- [[rag-ingestion-embeddings-retrieval]]
- [[financial-ner-extraction]]
- [[text-feature-engineering]]

## Sources

- [ch22_05_10k_rag_assistant.py](../../raw/articles/chung-khoan/ch22_05_10k_rag_assistant.py)
- [ch22_06_esg_rag_vs_finetune.py](../../raw/articles/chung-khoan/ch22_06_esg_rag_vs_finetune.py)
- [ch22_07_institutional_holdings_graph.py](../../raw/articles/chung-khoan/ch22_07_institutional_holdings_graph.py)
- [ch22_08_rag_security.py](../../raw/articles/chung-khoan/ch22_08_rag_security.py)
