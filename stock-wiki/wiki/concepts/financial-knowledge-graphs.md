---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch23_README.md]
---

# Financial Knowledge Graphs

Financial KGs represent entities as nodes, relationships as typed edges, and provenance as properties. They are useful when insight depends on explicit structure rather than fuzzy similarity across text chunks.

## When KGs Help

- Multi-hop supplier/customer chains
- Institutional ownership and co-ownership networks
- Contagion and spillover paths
- Temporal relationship changes
- Auditable evidence traversal

## Core Design Contracts

- Stable entity identity
- Compact ontology / finite relationship vocabulary
- Edge-level provenance
- Temporal timestamps: event, disclosure, extraction
- Query safety and schema versioning

## Links

- [[kg-construction-finance]]
- [[graph-rag-finance]]
- [[kg-features-gnn]]
- [[temporal-kg-leakage]]
- [[network-portfolio-construction]]
- [[rag-financial-research]]

## Sources

- [ch23_README.md](../../raw/articles/chung-khoan/ch23_README.md)
- [[ch23-knowledge-graphs]]
