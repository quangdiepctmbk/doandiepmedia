---
tags: [concept, strategy-definition, ml4t, reproducibility]
---

# Trial Taxonomy and Search Accounting

**§6.7** — Làm cho experimentation auditable và countable.

## Taxonomy

| Cấp độ | Ý nghĩa |
|--------|---------|
| **Strategy** | Ý tưởng chiến lược tổng thể |
| **Trial Family** | Nhóm các trial cùng hướng |
| **Trial** | Một configuration cụ thể |
| **Run** | Một lần chạy với seed cụ thể |

## Tại sao phải đếm?
- Biết bao nhiêu thứ đã thử → multiple testing correction
- Biết cái gì được chọn → selection bias
- Biết cái gì reserved → confirmation credibility

## Implementation
- Frozen config dataclass per notebook
- Auto-run logging (catalog JSON)
- Term sheets làm output artifact

## Links
- [[strategy-research-framework]]
- [[baseline-checkpoint]]
- [[strategy-term-sheet]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
- [exploration.md](../raw/articles/chung-khoan/ch06-strategy-definition-exploration.md)
