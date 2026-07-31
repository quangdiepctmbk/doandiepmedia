---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch23_06_gnn_feature_engineering.py
  - raw/articles/chung-khoan/ch23_09_knowledge_graph_features.py
  - raw/articles/chung-khoan/ch23_10_network_portfolio_construction.py
---

# KG Features, GNNs & Network Portfolio Construction

Graph structure can be transformed into leakage-aware tabular ML features and portfolio construction diagnostics.

## Graph-Derived Features (NB09)

- Supply-chain topology: PageRank, betweenness, degree, HHI
- 13F crowding and co-ownership
- Cross-graph interactions
- Output: tabular feature matrix for gradient-boosted models

## GNN Feature Engineering (NB06)

- Simplified GAT on stock correlation network
- Learn relational embeddings
- Compare tabular-only ridge vs hybrid model with GNN embeddings

## Network Portfolio Construction (NB10)

- Correlation networks + minimum spanning trees
- Asset centrality ranking
- Network-diversified portfolios
- Contagion simulation

## Links

- [[financial-knowledge-graphs]]
- [[kg-construction-finance]]
- [[portfolio-construction-ml]]
- [[hierarchical-risk-parity]]
- [[feature-design-grammar]]

## Sources

- [ch23_06_gnn_feature_engineering.py](../../raw/articles/chung-khoan/ch23_06_gnn_feature_engineering.py)
- [ch23_09_knowledge_graph_features.py](../../raw/articles/chung-khoan/ch23_09_knowledge_graph_features.py)
- [ch23_10_network_portfolio_construction.py](../../raw/articles/chung-khoan/ch23_10_network_portfolio_construction.py)
