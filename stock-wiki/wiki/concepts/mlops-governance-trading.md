---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch26_README.md]
---

# MLOps Governance for Trading

Post-deployment infrastructure that separates production-grade systems from research prototypes. Every deployed model decays — the operational difference is how quickly decay is detected and how safely the system responds.

## Three-Layer Governance Model

1. **Detection**: rolling metrics, drift diagnostics, online detectors
2. **Response**: shadow mode, cap-capped A/B, staged rollout
3. **Automated Safety**: multi-level circuit breakers (CLOSED/OPEN/HALF_OPEN)

## Technical vs Statistical Failure Taxonomy

- **Technical** failure: same inputs → different outputs (verification problem)
- **Statistical** failure: same outputs → no longer predict returns (performance problem)
- Conflating them wastes time and capital

## Links

- [[drift-monitoring-performance]]
- [[online-drift-detection]]
- [[safe-model-rollout]]
- [[circuit-breakers]]
- [[feast-feature-store]]
- [[mlflow-experiment-tracking]]
- [[live-trading-systems]]
- [[risk-management-ml]]

## Sources

- [ch26_README.md](../../raw/articles/chung-khoan/ch26_README.md)
- [[ch26-mlops-governance]]
