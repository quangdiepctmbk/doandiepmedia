---
type: concept
domain: trading
created: 2026-07-05
updated: 2026-07-05
sources: [macro-regimes-full-notebook]
---

# Macro Regime Detection

Phát hiện chế độ thị trường bằng macro indicators: thất nghiệp, Fed Funds, yield curve, CPI, VIX, credit spreads.

## Ý tưởng

Macro regimes không dự báo return tốt bằng việc phân biệt **volatility environments**. Chúng hữu ích để quản trị rủi ro hơn là timing thị trường.

## 4 regime từ core GMM

- **Expansion:** vol thấp nhất, annual vol 12.0%
- **Tightening:** Fed hiking / yield curve stress, annual vol 15.0%
- **Recovery:** rebound sau stress, annual vol 15.2%
- **Crisis:** unemployment shock / stress, annual vol 16.0% (chỉ 4 tháng sample)

## Tín hiệu quan trọng

- VIX spikes: 2008, 2020
- Initial claims: crisis peaks
- DFF: hiking cycles
- T10Y2Y: recession warnings trước 2008 và 2020

## Liên kết

- [[market-regimes]]
- [[ml4t-workflow]]
- [[factor-regimes]]
