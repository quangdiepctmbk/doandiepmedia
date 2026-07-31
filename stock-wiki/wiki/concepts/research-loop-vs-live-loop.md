---
tags: [concept, strategy-definition, ml4t]
---

# Research Loop vs Live Trading Loop

**§6.1** — Sự phân tách quan trọng nhất trong strategy research.

## Live Trading Loop
- Pipeline cố định (fixed parameters, fixed data sources)
- Chạy theo lịch (daily, weekly, monthly)
- Đầu vào: dữ liệu mới nhất
- Đầu ra: quyết định giao dịch

## Research Loop
- Cải tiến pipeline
- Đánh giá dưới cùng setup và protocol
- Không được làm nhiễu live loop
- Mỗi thay đổi là một trial mới

## Ý nghĩa
Nếu không tách bạch, bạn không biết một thay đổi là cải thiện thật hay do data snooping.

## Links
- [[strategy-research-framework]]
- [[walk-forward-evaluation]]
- [[evidence-boundary]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
