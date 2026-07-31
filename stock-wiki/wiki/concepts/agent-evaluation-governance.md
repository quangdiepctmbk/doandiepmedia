---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch24_09_evaluation_and_governance.py
  - raw/articles/chung-khoan/ch24_agent_observability.py
---

# Agent Evaluation, Observability & Governance

Decision-grade financial agents require proper scoring, replay, observability, contamination controls, and security gates.

## Evaluation (NB09)

- Brier score
- Log score
- Expected calibration error (ECE)
- Calibration curves
- Ablation experiments
- Replay with frozen tool responses

## Governance

- Point-in-time enforcement
- Contamination-aware testing
- Human approval boundaries
- Cost and latency monitoring
- Release discipline and drift monitoring

## Security Controls

- Warden proxy pattern for tool-call authorization
- Prompt injection defense
- Retrieval poisoning checks
- Least privilege
- OWASP Top 10 mapping for LLM applications

## Links

- [[financial-autonomous-agents]]
- [[react-tool-contracts-memory]]
- [[multi-agent-forecasting]]
- [[rag-security]]
- [[causal-validation-refutation]]

## Sources

- [ch24_09_evaluation_and_governance.py](../../raw/articles/chung-khoan/ch24_09_evaluation_and_governance.py)
- [ch24_agent_observability.py](../../raw/articles/chung-khoan/ch24_agent_observability.py)
