---
tags: [concept, strategy-definition, ml4t, evaluation, backtesting]
---

# Walk-Forward Evaluation Protocol

**§6.5** — Trung tâm phương pháp luận của chương. Biến "out-of-sample" từ slogan thành protocol với admissibility rules, chronology, governance.

## Tại sao IID CV không dùng được cho time series
- Financial returns không i.i.d (serial dependence, volatility clustering)
- Data leakage qua look-ahead bias
- Temporal ordering bị phá vỡ khi shuffle

## Kỹ thuật

| Kỹ thuật | Mô tả |
|----------|-------|
| **Walk-forward CV** | Train trên window, test trên next window, tuần tự |
| **Label buffer / Purging** | Loại bỏ label có overlap với test set |
| **Feature buffer / Embargo** | Loại bỏ feature bị contamination từ tương lai |
| **Calendar-aware splits** | Split theo thời gian thực, không random |
| **Nested walk-forward** | Validation set bên trong training window |
| **CPCV** | Combinatorial Purged Cross-Validation (Lopez de Prado 2018) |

## Mô hình 3 lớp
- **Model selection** → trên validation folds
- **Final estimation** → trên test holdout, chỉ đánh giá 1 lần
- **Sealed holdout** → không chạm vào cho đến khi hoàn thành research

## Links
- [[research-loop-vs-live-loop]]
- [[backtesting]]
- [[evidence-boundary]]
- [[cv-foundations]]
- [[deflated-sharpe-ratio]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
- [01_cv_foundations.py](../raw/articles/chung-khoan/ch06_01_cv_foundations.py)
