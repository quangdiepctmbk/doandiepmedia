---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch15_06_fed_announcement_bsts.py]
---

# BSTS Event Study (Bayesian Structural Time-Series)

Bayesian Structural Time-Series estimates the impact of discrete events by constructing data-driven counterfactuals from control series. Framed as: "what would have happened without this event?"

## How It Works

- Fit Bayesian state-space model on pre-event period: treated series = control series × coefficients + local trend + seasonality
- Predict counterfactual post-event (without treatment indicator)
- Difference between actual and counterfactual = causal impact

## Ch15 Application

NB06 studies 4 FOMC announcements on IEF Treasury ETF:

- Daily log returns as effect unit
- Per-event control-as-target and placebo checks
- Spillover risk: contaminated controls reduce credibility

## Limitations

- **Control spillover**: event can affect both treated and control → under/overestimate impact
- **Model-dependent**: different state-space priors → different impact estimates
- **Exchangeability assumption**: controls and treated must have stable relationship

## Links

- [[causal-ml-trading]]
- [[double-machine-learning]]
- [[causal-validation-refutation]]
- [[event-studies]]

## Sources

- [ch15_06_fed_announcement_bsts.py](../../raw/articles/chung-khoan/ch15_06_fed_announcement_bsts.py)
