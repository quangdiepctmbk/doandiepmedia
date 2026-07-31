---
tags: [concept, strategy-definition, ml4t]
---

# Trading Setup Definition

**§6.3** — Biến strategy map thành trading setup có version.

## Invariants (Fixed)

| Thành phần | Ý nghĩa |
|-------------|---------|
| Tradability rules | Cổ phiếu nào được giao dịch |
| Decision schedule | Khi nào ra quyết định |
| Score-to-trade mapping | Từ tín hiệu → danh mục |
| Constraints | Ràng buộc (position limits, leverage, sector) |
| Material costs | Phí, slippage, market impact |

## Parameter Tuning vs Mechanics Changes
- **Parameter tuning**: thay đổi trong cùng một setup (thresholds, lookback)
- **Mechanics change**: thay đổi cấu trúc strategy (tần suất, universe, cost model)
- Ranh giới này rất quan trọng để tránh overfitting

## 9 Case Studies
Trong notebook `02_case_study_overview`: ETF, crypto, intraday, AQR factors, futures, FX, options…

## Links
- [[strategy-map-edge]]
- [[strategy-term-sheet]]
- [[model-signal-strategy-metrics]]

## Sources
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
- [02_case_study_overview.py](../raw/articles/chung-khoan/ch06_02_case_study_overview.py)
