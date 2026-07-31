---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch24_01_react_reasoning.py
  - raw/articles/chung-khoan/ch24_02_tool_contracts.py
  - raw/articles/chung-khoan/ch24_03_state_and_memory.py
  - raw/articles/chung-khoan/ch24_agent_schemas.py
  - raw/articles/chung-khoan/ch24_agent_tools.py
---

# ReAct, Tool Contracts & Agent Memory

The foundation of reliable financial agents is explicit reasoning, typed tools, provenance-rich outputs, and replayable state.

## ReAct Reasoning (NB01)

- ReAct = reason + act loop
- Default because it is grounded and auditable
- Tree of Thoughts is reserved for branch-heavy decisions
- Reflexion requires explicit memory governance

## Tool Contracts (NB02)

- Typed schemas for inputs/outputs
- Multi-provider schema translation
- Provenance enrichment
- Domain policy enforcement
- Context engineering: expose only what the agent needs

## State & Memory (NB03)

- Working/short-term/long-term memory separation
- Typed state and quality gates
- Checkpointing and replay
- Schema versions for evolution

## Links

- [[financial-autonomous-agents]]
- [[multi-agent-forecasting]]
- [[agent-evaluation-governance]]
- [[rag-security]]

## Sources

- [ch24_01_react_reasoning.py](../../raw/articles/chung-khoan/ch24_01_react_reasoning.py)
- [ch24_02_tool_contracts.py](../../raw/articles/chung-khoan/ch24_02_tool_contracts.py)
- [ch24_03_state_and_memory.py](../../raw/articles/chung-khoan/ch24_03_state_and_memory.py)
- [ch24_agent_schemas.py](../../raw/articles/chung-khoan/ch24_agent_schemas.py)
- [ch24_agent_tools.py](../../raw/articles/chung-khoan/ch24_agent_tools.py)
