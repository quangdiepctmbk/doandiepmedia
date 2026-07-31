---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_03_label_methods.py]
---

# Label Engineering

Label engineering là thiết kế target cho bài toán học: forward return, excess return, volatility-scaled return, rank/quantile label, event label, hoặc barrier-based label.

## Definition

Notebook `03_label_methods.py` cho thấy label không chỉ là cột `y`. Label xác định horizon, direction, risk normalization, benchmark adjustment và cách model sẽ được đánh giá.

## Examples

- Forward return dùng để học hướng/lợi suất kỳ vọng trong horizon định trước.
- Excess return trừ benchmark để tách alpha khỏi market beta.
- Volatility-scaled label giúp so sánh across assets/regimes.
- Quantile/rank label phù hợp với cross-sectional ranking.
- Barrier/event label gắn với quản trị rủi ro và cấu trúc trade.

## Links

- [[learning-task-definition]]
- [[mfe-mae-analysis]]
- [[information-coefficient]]
- [[strategy-term-sheet]]

## Sources

- [Label methods source](../../raw/articles/chung-khoan/ch07_03_label_methods.py)
