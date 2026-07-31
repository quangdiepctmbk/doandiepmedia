---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch24_04_research_agent.py
  - raw/articles/chung-khoan/ch24_agent_research.py
  - raw/articles/chung-khoan/ch24_agent_pipeline.py
  - raw/articles/chung-khoan/ch24_agent_providers.py
---

# Evidence-First Research Agent Workflow

A constrained single-agent research workflow that gathers evidence, validates it, synthesizes, abstains when evidence is weak, and emits calibrated probability forecasts with metadata.

## Components

- Provider abstraction: Anthropic/OpenAI/Google/OpenRouter/Ollama/mock
- Search tools and source policy
- Quality gates for evidence sufficiency
- Forecast object with probability, rationale, citations, metadata
- Replayable artifacts for audit and scoring

## Design Principle

A research agent should not be judged by whether the write-up sounds convincing. It should be judged by provenance, probability calibration, abstention behavior, and replayability.

## Links

- [[financial-autonomous-agents]]
- [[react-tool-contracts-memory]]
- [[multi-agent-forecasting]]
- [[agent-evaluation-governance]]
- [[rag-financial-research]]

## Sources

- [ch24_04_research_agent.py](../../raw/articles/chung-khoan/ch24_04_research_agent.py)
- [ch24_agent_research.py](../../raw/articles/chung-khoan/ch24_agent_research.py)
- [ch24_agent_pipeline.py](../../raw/articles/chung-khoan/ch24_agent_pipeline.py)
- [ch24_agent_providers.py](../../raw/articles/chung-khoan/ch24_agent_providers.py)
