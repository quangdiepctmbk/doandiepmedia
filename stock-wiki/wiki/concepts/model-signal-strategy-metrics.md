---
tags: [concept, strategy-definition, ml4t, evaluation]
---

# Model, Signal, and Strategy Metrics

**§6.4** — "Better" phải được định nghĩa rõ ràng ở 3 cấp độ riêng biệt.

## Ba cấp độ diagnostics

| Cấp độ | Câu hỏi | Metric ví dụ |
|--------|---------|-------------|
| **Model diagnostics** | Model có học được pattern không? | R², accuracy, feature importance |
| **Signal diagnostics** | Pattern có translate thành tín hiệu giao dịch không? | IC, Sharpe ratio của signal, turnover |
| **Strategy outcomes** | Tín hiệu có sinh lợi nhuận thực không? | Net Sharpe, max DD, hit rate, costs |

## Tại sao phải tách?
- Không tối ưu micro-decision trực tiếp trên portfolio outcome → overfit
- Mỗi cấp độ có hypothesis test riêng
- Model tốt chưa chắc signal tốt, signal tốt chưa chắc strategy thắng

## Links
- [[strategy-research-framework]]
- [[walk-forward-evaluation]]
- [[evidence-boundary]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
