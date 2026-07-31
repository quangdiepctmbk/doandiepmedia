---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch23_03_graph_rag_qa.py
  - raw/articles/chung-khoan/ch23_04_rag_comparison_benchmark.py
---

# Graph RAG for Finance

Graph RAG uses deterministic relational retrieval from a graph database, then lets the LLM synthesize results. It is strongest for multi-hop, entity-specific, or relationship-heavy questions.

## Architecture

1. User question
2. Safe text-to-Cypher generation
3. Schema validation + read-only constraints
4. Deterministic database execution
5. LLM answer with cited graph evidence

## Ch23 Benchmarks

- **NB03 Graph RAG QA** — controlled text-to-Cypher over 13F holdings graph; read-only schema validation, dated queries, row limits
- **NB04 RAG comparison** — graph retrieval vs embedding retrieval on real 13F holdings; support recall and retrieval-token cost

## Safety Controls

- Read-only Cypher
- Whitelisted labels/relationships
- Row limits
- Dated queries / cutoff constraints
- No arbitrary write/delete operations

## Links

- [[financial-knowledge-graphs]]
- [[kg-construction-finance]]
- [[rag-financial-research]]
- [[temporal-kg-leakage]]

## Sources

- [ch23_03_graph_rag_qa.py](../../raw/articles/chung-khoan/ch23_03_graph_rag_qa.py)
- [ch23_04_rag_comparison_benchmark.py](../../raw/articles/chung-khoan/ch23_04_rag_comparison_benchmark.py)
