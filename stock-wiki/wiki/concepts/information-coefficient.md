---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_05_signal_evaluation.py]
---

# Information Coefficient

Information Coefficient (IC) đo tương quan giữa prediction/signal và realized return, thường dùng để đánh giá khả năng rank của signal trong cross-section hoặc theo thời gian.

## How It Works

Notebook `05_signal_evaluation.py` đặt IC cùng quantile returns và spreads như signal diagnostics. IC giúp trả lời signal có thứ tự hóa cơ hội tốt hơn ngẫu nhiên hay không, trước khi quy đổi thành strategy PnL.

## Practical Notes

IC nên được xem theo thời gian, regime, quantile và sau costs/constraints nếu có. IC trung bình nhỏ nhưng ổn định có thể có giá trị; IC cao nhưng tập trung trong một regime dễ là overfit.

## Links

- [[ic-inference]]
- [[model-signal-strategy-metrics]]
- [[factor-regimes]]
- [[multiple-testing-selection-bias]]

## Sources

- [Signal evaluation source](../../raw/articles/chung-khoan/ch07_05_signal_evaluation.py)
