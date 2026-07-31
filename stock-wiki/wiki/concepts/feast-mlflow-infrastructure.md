---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch26_05_feast_feature_store.py
  - raw/articles/chung-khoan/ch26_05b_feast_live.py
  - raw/articles/chung-khoan/ch26_06_mlflow_experiments.py
---

# Feast Feature Store & MLflow Experiment Tracking

MLOps infrastructure components for deployment-grade ML trading.

## NB05 — Feast Feature Store (Manual)

- Feature view definitions on real `us_equities_panel` feature tables
- Point-in-time offline join: 298k rows from 150k training events
- As-of online snapshot with lineage tracking
- Quantified training-serving skew: RSI mean abs delta 1.99, max 4.47

## NB05b — Feast Live Integration

- Feast end-to-end entity/feature view → offline/online retrieval
- 6 of 7 features match exactly with manual Polars implementation
- `garch_cond_vol` exposes vintage-tracking diagnostic
- Requires Feast ≥ 0.40

## NB06 — MLflow Experiment Tracking

- Walks `us_equities_panel` registry schema: training_runs, prediction_sets, backtest_runs, cohort_metrics
- Searchable experiment catalog from 50 training runs
- Ranking parity verified across 4 (family, label) spot-checks
- Governance value comes from disciplined run accounting, not specific tooling

## Links

- [[mlops-governance-trading]]
- [[drift-monitoring-performance]]
- [[safe-model-rollout]]
- [[ml-pipeline-registry]]

## Sources

- [ch26_05_feast_feature_store.py](../../raw/articles/chung-khoan/ch26_05_feast_feature_store.py)
- [ch26_05b_feast_live.py](../../raw/articles/chung-khoan/ch26_05b_feast_live.py)
- [ch26_06_mlflow_experiments.py](../../raw/articles/chung-khoan/ch26_06_mlflow_experiments.py)
