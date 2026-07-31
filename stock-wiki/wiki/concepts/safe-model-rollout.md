---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch26_03_safe_model_rollout.py]
---

# Safe Model Rollout Protocol

Response layer: how to update models in production without capital at risk.

## NB03 — Incumbent vs Candidate Rollout

Full protocol on real prediction artifacts:

1. **Selection**: train candidate on 2010–2014 data
2. **Shadow mode**: run candidate alongside incumbent without capital allocation
3. **Promotion criteria**: 5 explicit conditions
4. **Capital-capped A/B test**
5. **Staged allocation**: 10% → 25% allocation path
6. **Rollback** always available

Output: four-panel rollout dashboard (Figure 26.3).

## Links

- [[mlops-governance-trading]]
- [[drift-monitoring-performance]]
- [[circuit-breakers]]
- [[live-trading-systems]]
- [[risk-management-ml]]

## Sources

- [ch26_03_safe_model_rollout.py](../../raw/articles/chung-khoan/ch26_03_safe_model_rollout.py)
