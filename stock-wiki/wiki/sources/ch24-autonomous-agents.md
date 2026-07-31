---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch24_README.md
ingested: 2026-07-26
related_raw:
  - ch24_01_react_reasoning.py
  - ch24_02_tool_contracts.py
  - ch24_03_state_and_memory.py
  - ch24_04_research_agent.py
  - ch24_05_aggregation_math.py
  - ch24_06_multi_agent_research.py
  - ch24_07_adversarial_debate.py
  - ch24_08_forecasting_pipeline.py
  - ch24_09_evaluation_and_governance.py
  - ch24_10_framework_comparison.py
  - ch24_11_research_operator.py
  - ch24_agent_fixtures.py
  - ch24_agent_observability.py
  - ch24_agent_pipeline.py
  - ch24_agent_providers.py
  - ch24_agent_research.py
  - ch24_agent_schemas.py
  - ch24_agent_specialists.py
  - ch24_agent_tools.py
  - ch24_research_operator.py
---

# Autonomous Agents — Chương 24 (ML4T)

## Summary

Chương 24 chuyển từ prediction functions trên prepared datasets sang **agentic workflows**: hệ thống chủ động gather, filter, synthesize messy evidence trước khi đưa ra probability forecast. Tập trung vào read-only financial research/forecasting agents với traceability, replay, tool contracts, memory/state, multi-agent aggregation, evaluation/governance, và research operator.

11 notebooks + 9 support modules + README.

### Sections (10)

1. **24.1 Agentic Workflows** — agent useful khi bottleneck là evidence acquisition + structured judgment (NB01)
2. **24.2 Cognitive Architectures** — ReAct default, Tree of Thoughts cho branch-heavy, Reflexion khi có memory governance (NB01)
3. **24.3 Agent Memory** — typed state, checkpointing, replay, schema evolution (NB03)
4. **24.4 Tool Integration** — contracts, provenance, structured outputs, source policies (NB02)
5. **24.5 Framework Stack** — native SDK vs CrewAI vs LangGraph; visibility/replay/policy fit (NB10)
6. **24.6 Research Agent** — single-agent evidence-first workflow, quality gates, abstention, calibrated forecasts (NB04)
7. **24.7 Multi-Agent Forecasting** — aggregation math, temperature diversity, debate, supervisor, calibration (NB05-NB09)
8. **24.8 ML4T Research Operator** — thin orchestrator + general tools + skill consultation for next experiments (NB11)
9. **24.9 Production Prep** — observability, repeated-trial testing, contamination-aware evaluation, cost/latency control
10. **24.10 Security & Governance** — Warden pattern, prompt injection, retrieval poisoning, least privilege, human approval boundaries

### Key Takeaways

- Agents add value when data/evidence acquisition and judgment are the bottleneck — not when a stable tabular model already suffices.
- State/memory design is model-risk infrastructure: checkpoint, replay, schema versions, quality gates.
- Tool contracts often matter more than prompts: structured outputs + provenance + source policy.
- Multi-agent systems should be judged by probability quality, calibration, and ablation over baselines — not narrative sophistication.
- Production agent claims require observability, replay, point-in-time integrity, contamination controls, and security gates.

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 24
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/24_autonomous_agents)
- [[ch23-knowledge-graphs]] (previous chapter)
- [[rag-financial-research]], [[graph-rag-finance]]
