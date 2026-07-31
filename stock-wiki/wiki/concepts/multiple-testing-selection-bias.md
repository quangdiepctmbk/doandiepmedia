---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_07_multiple_testing.py]
---

# Multiple Testing and Selection Bias

Multiple testing và selection bias xuất hiện khi nhà nghiên cứu thử nhiều feature, label, model, universe hoặc horizon rồi chỉ giữ kết quả đẹp nhất.

## Definition

Chương 7 đưa multiple testing vào bước đánh giá signal. Vấn đề không nằm ở một backtest duy nhất, mà ở toàn bộ quá trình tìm kiếm: càng thử nhiều giả thuyết, xác suất false discovery càng cao.

## Controls

Các kiểm soát phù hợp gồm False Discovery Rate, Reality Check, SPA-style tests, sealed holdout, logging đầy đủ trial taxonomy, và so sánh với baseline. Điều này bổ sung cho [[deflated-sharpe-ratio]] ở tầng strategy outcome.

## Links

- [[deflated-sharpe-ratio]]
- [[baseline-checkpoint]]
- [[trial-taxonomy]]
- [[walk-forward-evaluation]]
- [[information-coefficient]]

## Sources

- [Multiple testing source](../../raw/articles/chung-khoan/ch07_07_multiple_testing.py)
