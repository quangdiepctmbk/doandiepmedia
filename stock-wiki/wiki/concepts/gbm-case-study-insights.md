---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_12_case_study_insights.py]
---

# GBM Case Study Insights

Meta-analysis của GBMs trên 9 asset classes từ ML4T: khi nào GBMs thực sự vượt linear models, và khi nào linear vẫn thắng.

## Findings (Ch12)

- **GBM > linear** trên hầu hết case studies — nonlinear structure có real edge
- **Ridge** vẫn thắng trên một số datasets — signal là diffuse, boosting chỉ thêm noise
- **Loss function và tree depth** quan trọng hơn library choice
- **Label design và horizon** ảnh hưởng nhiều hơn model class
- **Holdout decay** substantial — performance gap between validation and holdout
- **Linear/GBM/TabM three-way**: GBM trung tâm, TabM cạnh tranh khi temporal shift phức tạp

## Core Message

Nonlinear models often help — nhưng real edge đến từ matching **model, label, horizon, và evaluation design**, không phải từ GBM magic.

## Links

- [[gradient-boosting-trading]]
- [[ml-backtest-baseline]]
- [[regularized-regression-trading]]
- [[dl-vs-gbm-tabular]]
- [[walk-forward-evaluation]]

## Sources

- [ch12_12_case_study_insights.py](../../raw/articles/chung-khoan/ch12_12_case_study_insights.py)
