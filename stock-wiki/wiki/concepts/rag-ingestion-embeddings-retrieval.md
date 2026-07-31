---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch22_01_sec_filing_pipeline.py
  - raw/articles/chung-khoan/ch22_02_domain_embeddings_comparison.py
  - raw/articles/chung-khoan/ch22_03_hybrid_retrieval.py
  - raw/articles/chung-khoan/ch22_04_ragas_evaluation.py
---

# RAG Ingestion, Embeddings & Retrieval

Core building blocks of a financial RAG pipeline.

## SEC Filing Ingestion (NB01)

- Point-in-time metadata tagging
- Structure-aware parsing (tables, headers, temporal context)
- Chunking strategy: fixed-size fails tables/headers → structure-aware

## Domain Embeddings (NB02)

- Generic (openai, voyage) vs domain-adapted (FinBERT, sentence-transformers)
- Benchmark: FinMTEB, corpus-specific evaluation
- Trade-off: dimensionality, storage, latency

## Hybrid Retrieval (NB03)

- Vector search + BM25 lexical + metadata filtering
- Reciprocal Rank Fusion (RRF) for combining scores
- Practical default for financial query mix

## Evaluation (NB04)

- RAGAs: retrieval, context precision/recall, faithfulness, answer relevancy
- Separates: retrieval failure, context failure, synthesis failure, computation failure, abstention failure

## Links

- [[rag-financial-research]]
- [[10k-rag-assistant]]
- [[esg-rag-vs-finetune]]
- [[13f-holdings-graph]]

## Sources

- [ch22_01_sec_filing_pipeline.py](../../raw/articles/chung-khoan/ch22_01_sec_filing_pipeline.py)
- [ch22_02_domain_embeddings_comparison.py](../../raw/articles/chung-khoan/ch22_02_domain_embeddings_comparison.py)
- [ch22_03_hybrid_retrieval.py](../../raw/articles/chung-khoan/ch22_03_hybrid_retrieval.py)
- [ch22_04_ragas_evaluation.py](../../raw/articles/chung-khoan/ch22_04_ragas_evaluation.py)
