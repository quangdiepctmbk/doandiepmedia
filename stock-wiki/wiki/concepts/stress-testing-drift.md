---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch19_06_stress_testing.py
  - raw/articles/chung-khoan/ch19_07_drift_detection.py
---

# Stress Testing & Drift Detection

Two complementary approaches to finding strategy vulnerabilities before they manifest in production.

## Stress Testing (NB06)

- Historical crisis replay (2008, COVID, etc.)
- Hypothetical scenario construction (shock matrices)
- Reverse stress tests (what scenario would break the strategy?)
- Treat crises as regime exemplars

## Drift Detection (NB07)

When live data distribution ≠ training distribution, models silently degrade. Methods:
- Feature drift (distributional shift)
- Prediction drift (output distribution shift)
- Concept drift (X→y relationship changes)
- Adaptive thresholds, retraining triggers

## Links

- [[risk-management-ml]]
- [[var-cvar-path-risk]]
- [[factor-exposure-trade-shap]]
- [[ml-exit-signals]]
- [[deep-hedging]]

## Sources

- [ch19_06_stress_testing.py](../../raw/articles/chung-khoan/ch19_06_stress_testing.py)
- [ch19_07_drift_detection.py](../../raw/articles/chung-khoan/ch19_07_drift_detection.py)
