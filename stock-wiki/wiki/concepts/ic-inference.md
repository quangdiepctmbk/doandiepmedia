---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_06_ic_inference.py]
---

# IC Inference

IC inference đánh giá độ tin cậy thống kê của Information Coefficient, có điều chỉnh autocorrelation và dependence do dữ liệu tài chính thường overlap theo horizon/time.

## Definition

Notebook `06_ic_inference.py` dùng HAC adjustment và block bootstrap để tránh t-stat ngây thơ. Khi label có overlapping horizons hoặc signal được đo lặp lại theo ngày, observations không độc lập.

## Links

- [[information-coefficient]]
- [[walk-forward-evaluation]]
- [[multiple-testing-selection-bias]]
- [[deflated-sharpe-ratio]]

## Sources

- [IC inference source](../../raw/articles/chung-khoan/ch07_06_ic_inference.py)
