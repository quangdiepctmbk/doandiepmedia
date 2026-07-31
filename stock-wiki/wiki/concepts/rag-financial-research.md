---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch22_README.md]
---

# RAG for Financial Research

RAG grounds LLMs in verifiable evidence. In finance, hallucination is the central obstacle — RAG is the architectural answer.

## Pipeline Stages

1. **Ingestion** (NB01): structure-aware parsing, chunking, metadata, point-in-time filtering
2. **Embeddings** (NB02): domain-adapted models for jargon, entities, regulation
3. **Hybrid Retrieval** (NB03): vector search + lexical (BM25) + metadata + RRF
4. **Re-ranking & Prompting** (NB05): cross-encoder, citation-constrained, tool-verified compute
5. **Evaluation** (NB04): RAGAs — retrieval/context/synthesis/computation/abstention failures
6. **Security** (NB08): untrusted document corpora → adversarial attacks

## RAG vs Fine-Tune

- **RAG**: evidence-grounded reasoning over changing documents
- **Fine-tune**: repeatable label-producing skills

## Links

- [[sec-filing-ingestion]]
- [[domain-embeddings-finance]]
- [[hybrid-retrieval-rrf]]
- [[ragas-evaluation]]
- [[10k-rag-assistant]]
- [[esg-rag-vs-finetune]]
- [[13f-holdings-graph]]
- [[rag-security]]
- [[text-feature-engineering]]

## Sources

- [ch22_README.md](../../raw/articles/chung-khoan/ch22_README.md)
- [[ch22-rag-financial-research]]
