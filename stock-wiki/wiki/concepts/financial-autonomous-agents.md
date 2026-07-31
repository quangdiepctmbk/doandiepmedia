---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch24_README.md]
---

# Financial Autonomous Agents

Financial agents shift from fixed prediction functions to workflows that gather, filter, and synthesize messy evidence before producing a forecast. They are best suited for read-only decision support where traceability and provenance are more important than execution autonomy.

## When Agents Add Value

- Evidence acquisition is messy and multi-source
- Judgment requires synthesis rather than simple labels
- The output is a probability forecast or research memo
- Provenance, abstention, and replay are required

## When Not To Use Agents

- Stable structured input already feeds a conventional model
- Rules-based workflow is simpler and auditable
- Execution requires privileged live trading actions without strong controls

## Links

- [[react-financial-agents]]
- [[agent-state-memory-replay]]
- [[tool-contracts-provenance]]
- [[multi-agent-forecasting]]
- [[agent-evaluation-governance]]
- [[ml4t-research-operator]]
- [[rag-financial-research]]

## Sources

- [ch24_README.md](../../raw/articles/chung-khoan/ch24_README.md)
- [[ch24-autonomous-agents]]
