---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch12_README.md
ingested: 2026-07-26
related_raw:
  - ch12_01_ensemble_foundations.py
  - ch12_02_gbm_comparison.py
  - ch12_03_dl_vs_gbm.py
  - ch12_04_optuna_tuning.py
  - ch12_05_cross_library_hpo.py
  - ch12_06_optuna_multi_asset.py
  - ch12_07_hpo_comparison.py
  - ch12_08_shap_analysis.py
  - ch12_09_xai_limitations.py
  - ch12_10_shap_nlp_sentiment.py
  - ch12_11_conformal_gbm.py
  - ch12_12_case_study_insights.py
---

# Gradient Boosting & Advanced Tabular Models — Chương 12 (ML4T)

## Summary

Chương 12 systematic exploration của **Gradient Boosting Machines (GBMs)** cho trading: từ decision tree ensembles qua XGBoost/LightGBM/CatBoost comparison, HPO với Optuna, TreeSHAP interpretability, deep learning alternatives, đến cross-case-study meta-analysis.

12 notebooks chia làm 6 sections:

1. **12.1 Ensemble Foundations** — Random Forest vs GBM, bagging reduces variance, boosting reduces bias
2. **12.2 GBM Workhorse** — XGBoost/LightGBM/CatBoost: regularization, speed, categorical handling, learning-to-rank, monotonic constraints
3. **12.3 DL Alternatives** — TabPFN, TabM, TabR: khi nào neural nets đáng thay thế GBMs
4. **12.4 Advanced HPO** — Optuna TPE, pruning, multi-objective, walk-forward, cross-asset transfer
5. **12.5 SHAP & XAI** — TreeSHAP, interaction decomposition, Rashomon effect, NLP token-level attribution
6. **12.6 Nine Case Studies** — GBMs thường beat linear, nhưng đâu mới là real edge

## Key Takeaways

- **GBMs > Random Forests** trên hầu hết case studies — sequential error correction beats variance reduction alone
- **LightGBM vs XGBoost vs CatBoost** — spread nhỏ, chọn theo categorical structure, compute, latency
- **GBMs > linear models** khi có nonlinear/threshold structure, nhưng linear vẫn thắng nếu signal là diffuse
- **Walk-forward HPO** là mandatory — single-fold HPO overestimates performance
- **TabPFN/TabM/TabR** — triển vọng nhưng chưa thay thế GBMs cho tabular financial data
- **TreeSHAP** powerful nhưng cần biết Rashomon effect: similar predictions ≠ similar explanations
- **Multi-objective HPO** (IC vs turnover) — tối ưu cả predict power lẫn transaction cost
- **Conformal prediction** cho GBMs — split, QR-conformal, CQR với empirical coverage

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 12
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/12_gradient_boosting)
- [[ch11-ml-pipeline]] (previous chapter)
