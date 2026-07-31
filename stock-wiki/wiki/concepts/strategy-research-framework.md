---
tags: [concept, strategy-definition, ml4t]
---

# Strategy Research Framework

**Chương 6** của ML4T. Luận điểm cốt lõi: trading strategy không chỉ là signal hay model, mà là một **quy trình ra quyết định có thể thực thi được**, phải được định nghĩa tại thời điểm quyết định và đánh giá như thể đang chạy thật.

## Hai vòng lặp

| Vòng lặp | Mục đích | Nhịp |
|-----------|----------|------|
| **Live trading loop** | Thực thi pipeline cố định trên dữ liệu mới | Theo lịch cố định |
| **Research loop** | Cải tiến pipeline dưới cùng một setup và evaluation protocol | Linh hoạt |

## Quy trình 7 bước từ Idea → Evidence

1. Mapping strategy (§6.2)
2. Trading setup versioned (§6.3)
3. Objectives & metrics (§6.4)
4. Evaluation protocol (§6.5)
5. Baseline checkpoint (§6.6)
6. Search expansion
7. Run logging (§6.7)

## Links
- [[research-loop-vs-live-loop]]
- [[strategy-map-edge]]
- [[machine-learning-for-trading]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
