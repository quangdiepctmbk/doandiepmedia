---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch23_07_dynamic_kg_temporal.py]
---

# Temporal KG Leakage Controls

Temporal knowledge graphs require explicit cutoff logic because relationships can exist economically before they are disclosed or extracted.

## Three-Timestamp Model

1. **Event time** — when the underlying relationship/event happened
2. **Disclosure time** — when market could observe it
3. **Extraction time** — when the pipeline added it to the graph

Backtests and feature generation must respect the relevant cutoff, usually disclosure time or extraction time depending on research question.

## NB07

Builds leakage-safe temporal snapshots from the 8-K event graph, separating event/disclosure/extraction time, measuring relationship churn and centrality drift, and verifying no post-cutoff leakage.

## Links

- [[financial-knowledge-graphs]]
- [[graph-rag-finance]]
- [[kg-construction-finance]]
- [[walk-forward-evaluation]]

## Sources

- [ch23_07_dynamic_kg_temporal.py](../../raw/articles/chung-khoan/ch23_07_dynamic_kg_temporal.py)
