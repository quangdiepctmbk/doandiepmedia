---
tags: [concept, strategy-definition, ml4t, tooling]
---

# Strategy Term Sheet

Mẫu specification có cấu trúc cho trading strategy, triển khai dưới dạng Python dataclass.

## Cấu trúc StrategyTermSheet

| Field | Type | Mô tả |
|-------|------|-------|
| `name` | str | Tên strategy |
| `version` | str | Version |
| `status` | Draft \| Review \| Approved | |
| `classification` | Price-Based \| Fundamental \| Structural \| ML-Enhanced | |
| `hypothesis` | FalsifiableHypothesis | Giả thuyết có thể bác bỏ |
| `blueprint` | ImplementationBlueprint | Chi tiết implement |
| `feasibility` | FeasibilityGate | Tính khả thi |
| `validation` | ValidationPlan | Kế hoạch kiểm định |

## 8 Term Sheets hoàn chỉnh
ETF momentum, crypto premium reversal, intraday orderflow reversal, cross-sectional factor momentum, futures carry, FX momentum, options vol alpha, ETF momentum (legacy)

## Pattern: Frozen Config Dataclass
```python
@dataclass(frozen=True)
class EtfExplorationConfig:
    start_date_str: str = "2007-01-01"
    momentum_formation_days: int = 126
    skip_month_days: int = 21
```

## Links
- [[trading-setup-definition]]
- [[trial-taxonomy]]
- [[strategy-map-edge]]

## Sources
- [exploration.md](../raw/articles/chung-khoan/ch06-strategy-definition-exploration.md)
- [README Chương 6](../raw/articles/chung-khoan/ch06-strategy-definition-readme.md)
