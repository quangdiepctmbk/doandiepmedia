---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_07_event_studies.py]
---

# Event Studies

Event studies measure abnormal returns around specific events: signal triggers, macro announcements, earnings. Key validation technique cho trading signals.

## Methodology

1. **Event Generation** — define event window, estimation window, và event types
2. **Market Model Estimation** — regression of stock returns on market returns (estimation window)
3. **Abnormal Returns (AR)** — actual return minus expected return (market model)
4. **Average Abnormal Return (AAR)** — cross-sectional average AR
5. **Cumulative Average Abnormal Return (CAAR)** — tich lũy AAR qua event window
6. **CAR Distribution** — t-test và cross-sectional variability

## Confidence Bands

CAAR cần confidence bands (parametric hoặc bootstrap) để biết abnormal return có ý nghĩa thống kê không.

## Links

- [[learning-task-definition]]
- [[causal-sanity-checks]]
- [[information-coefficient]]
- [[strategy-research-framework]]

## Sources

- [Event studies source](../../raw/articles/chung-khoan/ch08_07_event_studies.py)
