---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_README.md]
---

# Feature Design Grammar

Feature design grammar là khuôn khổ chuyển trading narrative thành feature specification có kỷ luật: khởi tạo từ economic hypothesis, không phải từ indicator collecting.

## Definition (3-Step Filter)

1. **Horizon Alignment** — feature phải cùng horizon với decision/target, hoặc có role rõ ràng khác (state vs signal).
2. **Driver Hypothesis** — feature cần gắn liền với economic mechanism cụ thể, không phải là "thử xem có dùng được không".
3. **Role Separation** — signal feature (dự báo), state variable (điều kiện), hay context variable (mô tả). Mỗi role có cách đánh giá khác.

## Design Knobs

- Reference frame (absolute, relative, cross-sectional, risk-adjusted)
- Representation (returns, ranks, quantiles, z-scores)
- Aggregation (mean, rolling, decay-weighted, PCA components)
- Point-in-time constraint (for slow-moving data)

## Links

- [[price-volume-features]]
- [[microstructure-features]]
- [[structural-cross-instrument-features]]
- [[slow-moving-contextual-features]]
- [[strategy-research-framework]]

## Sources

- [Chapter 8 README](../../raw/articles/chung-khoan/ch08_README.md)
