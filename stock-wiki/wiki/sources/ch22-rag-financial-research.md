---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch22_README.md
ingested: 2026-07-26
related_raw:
  - ch22_01_sec_filing_pipeline.py
  - ch22_02_domain_embeddings_comparison.py
  - ch22_03_hybrid_retrieval.py
  - ch22_04_ragas_evaluation.py
  - ch22_05_10k_rag_assistant.py
  - ch22_06_esg_rag_vs_finetune.py
  - ch22_07_institutional_holdings_graph.py
  - ch22_08_rag_security.py
---

# RAG for Financial Research — Chương 22 (ML4T)

## Summary

Chương 22 dùng Retrieval-Augmented Generation (RAG) cho financial research. LLMs grounded in verifiable evidence — không phải oracle. Từ SEC filing ingestion → domain embeddings → hybrid retrieval → re-ranking → RAG evaluation → 10-K assistant → ESG vs fine-tune → institutional holdings graph → RAG security → agentic frameworks.

8 notebooks.

### Sections (9):

1. **22.1 Generative Leap**: text classification không đủ cho open-ended analyst questions
2. **22.2 RAG Architecture**: index → retrieve → generate pipeline
3. **22.3 Intelligent Ingestion**: structure-aware parsing, chunking, metadata (NB01)
4. **22.4 Domain Embeddings**: domain-adapted vs generic embedding models (NB02)
5. **22.5 Hybrid Retrieval**: vector search + lexical + metadata filtering + RRF (NB03)
6. **22.6 Re-ranking & Prompting**: cross-encoder, citation-constrained, tool-verified compute (NB05)
7. **22.7 Diagnosing Bottlenecks**: retrieval/context/synthesis/computation/abstention failures; RAGAs (NB04, NB08)
8. **22.8 Applications**: 10-K assistant, ESG RAG vs fine-tune, 13F holdings graph (NB05-07)
9. **22.9 Agentic Frameworks**: RAG as tool inside multi-step agent workflows

### Key Takeaways

- **Hallucination là central obstacle** → RAG grounds LLM in verifiable evidence
- **Poor ingestion silently corrupts downstream**: chunking, metadata, temporal tags
- **Domain embeddings matter**: generic models fail on jargon, entities, regulation
- **Hybrid retrieval** (semantic + lexical + metadata) = practical default
- **RAG ≠ fine-tune**: RAG for evidence-grounded reasoning; fine-tune for repeatable label skills
- **RAG security**: untrusted document corpora can poison responses (NB08)
- **Agentic frameworks**: RAG as tool inside controller-tool-memory pattern

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 22
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/22_rag_financial_research)
- [[ch21-rl-execution-hedging]] (previous chapter)
- [[ch10-text-feature-engineering]] (text features, NLP overlap)
