---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_02_preprocessing_pipeline.py]
---

# Train-Only Preprocessing

Train-only preprocessing là nguyên tắc fit mọi transformer, scaler, imputer, encoder và outlier rule chỉ trên training data, sau đó chỉ transform validation/test/live data.

## Definition

Chương 7 nhấn mạnh preprocessing phải là protocol-safe. Việc dùng toàn bộ sample để tính median, standard deviation, quantile cap hoặc imputation rule có thể làm thông tin tương lai lọt vào quá khứ.

## How It Fits

Nguyên tắc này liên kết trực tiếp với [[walk-forward-evaluation]]: mỗi window nghiên cứu phải fit preprocessing từ phần train của window đó. Nó cũng hỗ trợ audit vì từng rule có thể được versioned trong [[trading-setup-definition]].

## Links

- [[walk-forward-evaluation]]
- [[trading-setup-definition]]
- [[data-quality-diagnostics]]
- [[learning-task-definition]]

## Sources

- [Preprocessing pipeline source](../../raw/articles/chung-khoan/ch07_02_preprocessing_pipeline.py)
