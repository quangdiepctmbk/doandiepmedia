---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch26_01_drift_monitoring.py
  - raw/articles/chung-khoan/ch26_02_online_drift_detection.py
---

# Drift Monitoring & Online Detection

Detection layer of post-deployment governance: rolling metrics, data drift diagnostics, and online concept-drift detectors.

## NB01 — Drift Monitoring Dashboard

Four-panel operational dashboard:
- Per-feature PSI bars
- Baseline-vs-current prediction-score histogram
- Rolling 63-day IC
- Rolling 63-day hit rate

Alert states wired to configurable K-S p-value threshold.

## NB02 — Online Drift Detection

- ADWIN-style (two-window mean-shift)
- DDM detectors
- Runs on real chronological validation-error streams for OLS and ridge linear models
- Reports signed lead/lag against equal-weight market-stress proxy

## Links

- [[mlops-governance-trading]]
- [[safe-model-rollout]]
- [[circuit-breakers]]
- [[risk-management-ml]]
- [[stress-testing-drift]]

## Sources

- [ch26_01_drift_monitoring.py](../../raw/articles/chung-khoan/ch26_01_drift_monitoring.py)
- [ch26_02_online_drift_detection.py](../../raw/articles/chung-khoan/ch26_02_online_drift_detection.py)
