---
tags: [concept, strategy-definition, ml4t, evaluation, backtesting]
---

# Cross-Validation Foundations for Time Series

**Notebook 01** — Walk-forward CV từ first principles.

## Kỹ thuật chính

- **Decision-time admissibility**: chỉ dùng dữ liệu có sẵn tại thời điểm quyết định
- **Label buffer (purging)**: loại observation có label overlap với test window
- **Feature buffer (embargo)**: loại observation bị contamination bởi tương lai
- **Calendar-aware splits**: split dựa trên calendar, không random
- **Nested walk-forward**: validation fold bên trong training fold
- **CPCV (Combinatorial Purged CV)**: nhiều path của walk-forward, kết hợp combinatorial

## Code patterns (Polars)
- Time-based forward returns: dùng `join_asof` với tolerance thay vì `.shift()`
- Event study với cooldown: stateful thinning, so sánh với last KEPT event

## Links
- [[walk-forward-evaluation]]
- [[backtesting]]
- [[evidence-boundary]]
- [[deflated-sharpe-ratio]]

## Sources
- [01_cv_foundations.py](../raw/articles/chung-khoan/ch06_01_cv_foundations.py)
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
