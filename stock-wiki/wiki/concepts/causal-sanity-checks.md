---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_08_causal_sanity_checks.py]
---

# Causal Sanity Checks

Causal sanity checks là kiểm tra cơ chế hợp lý của feature/signal trước khi đưa sâu vào pipeline nghiên cứu.

## Definition

Notebook `08_causal_sanity_checks.py` không chứng minh nhân quả đầy đủ, nhưng buộc signal phải có câu chuyện vận hành hợp lý: thông tin có sẵn đúng thời điểm, tác động không phải artifact của leakage, và quan hệ không chỉ do confounder/regime đơn giản.

## Role In Research

Sanity checks giúp triage feature trước khi tốn chi phí modeling/backtesting. Chúng phù hợp với [[evidence-boundary]]: phân biệt bằng chứng cơ chế, bằng chứng thống kê và bằng chứng strategy outcome.

## Links

- [[evidence-boundary]]
- [[learning-task-definition]]
- [[information-coefficient]]
- [[strategy-research-framework]]

## Sources

- [Causal sanity checks source](../../raw/articles/chung-khoan/ch07_08_causal_sanity_checks.py)
