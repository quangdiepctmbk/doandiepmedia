---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_04_fundamentals_macro_calendar.py]
---

# Slow-Moving and Contextual Features

Fundamentals, macro indicators, and calendar encodings làm state variables điều kiện hóa signal nhanh. Chậm nhưng nguy hiểm hơn data nhanh vì reporting lags, revisions và repeated values.

## Components

- **Fundamentals (SEC XBRL)**: value factors (E/P, B/P, CF/P), quality factors (ROE, gross profitability, accruals); point-in-time ASOF join là mandatory
- **Macro (FRED)**: yield curve slope, VIX regime, credit spread; publication-lag handling và monthly forward-fill
- **Risk Regime Features**: Markov regime probability, volatility regime
- **Calendar Encodings**: cyclical sin/cos encoding, time-to-event proximity (days-to-next-FOMC)

## Key Principles

- ASOF join: mỗi daily observation chỉ thấy most recent monthly snapshot
- Publication lag: macro data KHÔNG available ngay tại period end
- Inflated sample-size trap: monthly char → daily join làm tăng N ảo

## Links

- [[feature-design-grammar]]
- [[structural-cross-instrument-features]]
- [[financial-data-universe]]

## Sources

- [Fundamentals/macro/calendar source](../../raw/articles/chung-khoan/ch08_04_fundamentals_macro_calendar.py)
