---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch24_10_framework_comparison.py
  - raw/articles/chung-khoan/ch24_11_research_operator.py
  - raw/articles/chung-khoan/ch24_research_operator.py
---

# ML4T Research Operator

The ML4T Research Operator is a thin orchestrator that gives a language model a small set of general-purpose tools and lets it execute the next experiment for Chapter 20 case studies.

## Framework Comparison (NB10)

Compares equivalent forecasting workflows in:

- Native Python SDK
- CrewAI role-based workflow
- LangGraph state graph

Selection criterion: state visibility, replayability, policy enforcement, and debugging quality — not framework hype.

## Research Operator (NB11)

- ≈880-line orchestrator
- 10 general-purpose tools: read/write/edit files, run bash, SQLite registry, inspect Parquet, consult skills
- On-demand skill consultation keeps prompt short while methodology grows
- Replays two captured DeepSeek traces: ETF ensemble experiment and small-cap universe filter
- Recovers backtest specification from registry and reruns under identical cost-aware configuration

## Links

- [[financial-autonomous-agents]]
- [[strategy-synthesis-pipeline]]
- [[research-agent-workflow]]
- [[agent-evaluation-governance]]
- [[hermes-agent]]

## Sources

- [ch24_10_framework_comparison.py](../../raw/articles/chung-khoan/ch24_10_framework_comparison.py)
- [ch24_11_research_operator.py](../../raw/articles/chung-khoan/ch24_11_research_operator.py)
- [ch24_research_operator.py](../../raw/articles/chung-khoan/ch24_research_operator.py)
