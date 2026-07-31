---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch26_README.md
ingested: 2026-07-26
related_raw:
  - ch26_01_drift_monitoring.py
  - ch26_02_online_drift_detection.py
  - ch26_03_safe_model_rollout.py
  - ch26_04_circuit_breakers.py
  - ch26_05_feast_feature_store.py
  - ch26_05b_feast_live.py
  - ch26_06_mlflow_experiments.py
---

# MLOps and Governance — Chương 26 (ML4T)

## Summary

Chương 26 xây dựng post-deployment infrastructure cho live ML trading systems. Mô hình nào cũng decay (regime shifts, competition erodes signal). Sự khác biệt giữa profitable và capital-destroying là tốc độ phát hiện decay và độ an toàn khi response.

7 notebooks + README.

### Sections (7)

1. **26.1 Two Failure Sources** — technical vs statistical failure taxonomy
2. **26.2 Performance Monitoring** — rolling IC, hit rate, backtest-to-live realization ratio (NB01)
3. **26.3 Drift Detection** — PSI, K-S, SHAP feature drift, ADWIN, DDM (NB01–02)
4. **26.4 Safe Model Updates** — shadow mode, cap-capped A/B, staged rollout, promote/reject criteria, rollback (NB03)
5. **26.5 Circuit Breakers** — drawdown/loss/consecutive-loss/latency; CLOSED/OPEN/HALF_OPEN (NB04)
6. **26.6 MLOps Infrastructure** — Feast feature store, MLflow experiment tracking, data versioning, model registry (NB05–06)
7. **26.7 Summary** — three-layer governance model

### Key Takeaways

- **Technical vs Statistical failure** — diagnostics differ; conflating wastes resources.
- **Drift monitoring**: PSI/K-S for data drift, SHAP for feature drift, ADWIN/DDM for concept drift.
- **Safe rollout**: shadow mode → capital-capped A/B → staged allocation. Rollback always available.
- **Circuit breakers**: multi-level, stateful (CLOSED/OPEN/HALF_OPEN), with manager event log.
- **MLOps infrastructure** should be right-sized to team maturity, not adopted wholesale.

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 26
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/26_mlops_governance)
- [[ch25-live-trading]] (previous chapter)
