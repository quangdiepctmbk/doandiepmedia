---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch13_12_case_study_insights.py]
---

# DL Case Study Insights

Cross-case-study meta-analysis: DL wins clearly in only a narrow part of ML4T's evidence base, simple sequence models often beat elaborate forecasting architectures, and strong tabular baselines remain hard to dislodge.

## Key Findings

- **LSTM** is the strongest DL baseline — simple, reliable, hard to beat for TS
- **PatchTST** adds value on datasets with clear local temporal patterns
- **iTransformer** useful when cross-variate dependencies dominate
- **TCN > LSTM** in speed but limited very-long-range
- **TSMixer** competitive with attention despite MLP-only
- **Mamba** promising for long sequences (O(T))
- **DL vs GBM** picture mixed: GBMs still win on many tabular problems; DL wins when temporal structure is complex and dataset large enough
- **Holdout decay** substantial — always confirm findings on sealed data

## Practitioner Bottom Line

Tabular baseline (Ridge → GBM) first. DL complexity only justified when simple baselines have demonstrably hit ceiling.

## Links

- [[dl-time-series-forecasting]]
- [[ml-backtest-baseline]]
- [[gradient-boosting-trading]]
- [[regularized-regression-trading]]
- [[walk-forward-evaluation]]

## Sources

- [ch13_12_case_study_insights.py](../../raw/articles/chung-khoan/ch13_12_case_study_insights.py)
