---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch24_05_aggregation_math.py
  - raw/articles/chung-khoan/ch24_06_multi_agent_research.py
  - raw/articles/chung-khoan/ch24_07_adversarial_debate.py
  - raw/articles/chung-khoan/ch24_08_forecasting_pipeline.py
  - raw/articles/chung-khoan/ch24_agent_specialists.py
  - raw/articles/chung-khoan/ch24_agent_fixtures.py
---

# Multi-Agent Forecasting Systems

Multi-agent forecasting combines multiple research agents, aggregation, debate, supervisor review, calibration, and outcome scoring.

## Aggregation Math (NB05)

- Neyman extremization
- Weighted aggregation
- Log-odds calibration
- `find_optimal_d` tuned on resolved forecasts

## Multi-Agent Research (NB06)

- Run N agents in parallel
- Identical agents with temperature diversity can produce useful diversity even without role specialization

## Adversarial Debate (NB07)

- Bull vs bear arguments
- Stress-test consensus by forcing explicit opposing cases
- Measure probability convergence/divergence after debate

## Full Forecasting Pipeline (NB08)

- agent → aggregation → debate → supervisor
- AIA-style forecaster
- Multiple resolved questions with full trace output

## Links

- [[financial-autonomous-agents]]
- [[research-agent-workflow]]
- [[agent-evaluation-governance]]
- [[evidence-boundary]]

## Sources

- [ch24_05_aggregation_math.py](../../raw/articles/chung-khoan/ch24_05_aggregation_math.py)
- [ch24_06_multi_agent_research.py](../../raw/articles/chung-khoan/ch24_06_multi_agent_research.py)
- [ch24_07_adversarial_debate.py](../../raw/articles/chung-khoan/ch24_07_adversarial_debate.py)
- [ch24_08_forecasting_pipeline.py](../../raw/articles/chung-khoan/ch24_08_forecasting_pipeline.py)
- [ch24_agent_specialists.py](../../raw/articles/chung-khoan/ch24_agent_specialists.py)
- [ch24_agent_fixtures.py](../../raw/articles/chung-khoan/ch24_agent_fixtures.py)
