---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch11_README.md
ingested: 2026-07-26
related_raw:
  - ch11_01_ols_inference.py
  - ch11_02_regularization_paths.py
  - ch11_03_logistic_classification.py
  - ch11_04_nested_cv_hpo.py
  - ch11_05_shap_analysis.py
  - ch11_06_conformal_prediction.py
  - ch11_07_case_study_insights.py
  - ch11_08_ml_backtest_intro.py
---

# The Machine Learning Pipeline — Chương 11 (ML4T)

## Summary

Chương này xây dựng full **ML pipeline cho trading**: từ linear baselines (OLS → Ridge / LASSO / Elastic Net) qua logistic classification, SHAP interpretability, conformal prediction, cho đến backtest validation. Đây là chương đặt nền tảng: mọi model phức tạp hơn ở các chương sau đều phải beat baseline này.

8 notebooks chia làm 6 sections:

1. **11.1 From Inference to Prediction** — Tại sao unbiased parameter recovery không phải mục tiêu chính trong trading; thay vào đó là stable OOS forecasts.
2. **11.2 Regularized Regression** — Ridge, LASSO, Elastic Net với walk-forward CV, leakage-safe standardization, Optuna HPO.
3. **11.3 Logistic Classification** — Direction prediction thay vì magnitude prediction, calibration, class imbalance.
4. **11.4 SHAP Interpretability** — SHAP values cho linear models, feature attribution stability, debugging wrong predictions.
5. **11.5 Conformal Prediction** — Prediction intervals finite-sample valid, coverage monitoring dưới non-stationary conditions.
6. **11.6 Linear Models Across Nine Case Studies** — Meta-analysis: khi nào linear models đủ tốt, khi nào cần phức tạp hơn.

## Notebooks

| Notebook | Content |
|----------|---------|
| 01_ols_inference | Classical OLS: coefficient significance, Gauss-Markov diagnostics, robust SE |
| 02_regularization_paths | Ridge/LASSO/Elastic Net walk-forward trên 100 ETFs, 21-day forward returns |
| 03_logistic_classification | Predict up/down direction, probability → position sizing |
| 04_nested_cv_hpo | Alpha-grid sweep + Optuna, nested vs single-loop CV (selection bias) |
| 05_shap_analysis | SHAP decomposition: βⱼ·(xⱼ−x̄ⱼ) cho linear models |
| 06_conformal_prediction | Split-conformal, adaptive conformal inference, CQR |
| 07_case_study_insights | 9 case studies meta-analysis: IC, turnover, net returns |
| 08_ml_backtest_intro | ML vs momentum baseline, IC ≠ portfolio profitability |

## Key Takeaways

- **Ridge outperforms LASSO/Elastic Net** trên hầu hết case studies — diffuse signal phù hợp regularized shrinkage hơn sparse selection
- **Walk-forward là mandatory** — fit standardization + preprocessing inside each expanding window
- **Nested CV quantifies selection bias** — single-loop HPO inflates performance estimates significantly
- **IC ≠ portfolio alpha** — NB08 chứng minh positive IC bị turnover + transaction costs xóa sổ
- **Linear models là baseline bắt buộc** — nếu linear không có signal, phức tạp hơn cũng vô ích
- **Conformal prediction** cần monitoring vì financial data violate exchangeability

## Reference

- Stefan Jansen, Machine Learning for Trading (2nd ed.), Ch. 11
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/11_ml_pipeline)
- [[ch10-text-feature-engineering]] (previous chapter)
