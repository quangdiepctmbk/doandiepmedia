---
type: concept
domain: trading-research
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_04_maximum_favorable_adverse_excursion.py]
---

# MFE/MAE Analysis

MFE/MAE analysis đo Maximum Favorable Excursion và Maximum Adverse Excursion sau entry để hiểu đường đi của trade, không chỉ kết quả cuối kỳ.

## Definition

MFE là mức di chuyển thuận lợi nhất trong thời gian giữ vị thế; MAE là mức di chuyển bất lợi nhất. Notebook Chương 7 dùng chúng để đánh giá path risk, stop/target logic và chất lượng entry.

## Why It Matters

Một signal có return cuối kỳ tốt nhưng MAE lớn có thể khó giao dịch thực tế. Ngược lại, MFE cao nhưng closing return thấp có thể gợi ý vấn đề exit rule. Vì vậy MFE/MAE nối [[label-engineering]] với [[quan-tri-rui-ro]].

## Links

- [[label-engineering]]
- [[quan-tri-rui-ro]]
- [[trading-setup-definition]]

## Sources

- [MFE/MAE source](../../raw/articles/chung-khoan/ch07_04_maximum_favorable_adverse_excursion.py)
