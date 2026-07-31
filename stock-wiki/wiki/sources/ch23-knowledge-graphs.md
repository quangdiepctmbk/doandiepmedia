---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch23_README.md
ingested: 2026-07-26
related_raw:
  - ch23_01_sp100_sec_download.py
  - ch23_02_supply_chain_kg_construction.py
  - ch23_03_graph_rag_qa.py
  - ch23_04_rag_comparison_benchmark.py
  - ch23_05_institutional_holdings_kg.py
  - ch23_06_gnn_feature_engineering.py
  - ch23_07_dynamic_kg_temporal.py
  - ch23_08_8k_event_extraction.py
  - ch23_09_knowledge_graph_features.py
  - ch23_10_network_portfolio_construction.py
---

# Knowledge Graphs for Financial AI — Chương 23 (ML4T)

## Summary

Chương 23 mở rộng từ vector RAG sang **knowledge graphs**: entities là nodes, relationships là typed edges, provenance là properties. Graphs hữu ích khi câu hỏi cần multi-hop reasoning, ownership chains, supplier networks, contagion paths, hoặc timing của relationship changes.

10 notebooks + README.

### Sections (7):

1. **23.1 When Graphs Matter** — graphs earn overhead when question is multi-hop, crowded, or temporal
2. **23.2 KG Construction** — LLM extraction + identity/schema/provenance contracts (NB01, NB02, NB05, NB08)
3. **23.3 Graph RAG** — deterministic relational retrieval; safe text-to-Cypher (NB03, NB04)
4. **23.4 Graph Features** — centrality, crowding, co-ownership, cross-graph interactions (NB09)
5. **23.5 Financial Networks** — MST/correlation networks, GNN embeddings, network-diversified portfolios (NB06, NB10)
6. **23.6 Temporal Integrity** — event/disclosure/extraction timestamps; cutoff-safe features (NB07)
7. **23.7 Engineering Decisions** — Neo4j, ontology scope, schema versioning, query safety

### Key Takeaways

- **Graph overhead is justified** for relational, multi-hop, temporal questions — not every RAG problem needs a KG
- **KG construction is governance**: stable entity IDs, finite relationship vocabulary, edge-level provenance
- **Graph RAG** delegates relational logic to database, language synthesis to LLM
- **Temporal leakage control** needs 3 timestamps: event time, disclosure time, extraction time
- **Graph features** become tabular ML inputs: PageRank, betweenness, HHI, co-ownership, crowding
- **Network portfolio construction** uses correlation MST and centrality to diversify/diagnose contagion

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 23
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/23_knowledge_graphs)
- [[ch22-rag-financial-research]] (previous chapter)
