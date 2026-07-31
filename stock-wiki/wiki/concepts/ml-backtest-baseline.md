---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch11_README.md
  - raw/articles/chung-khoan/ch11_07_case_study_insights.py
  - raw/articles/chung-khoan/ch11_08_ml_backtest_intro.py
---

# ML Backtest Baseline

IC, signal accuracy, and model diagnostics are necessary but not sufficient — the ultimate test is whether ML signals translate to net portfolio returns after turnover and transaction costs.

## Key Lesson from Ch11

NB08 demonstrates that **positive IC does not guarantee portfolio profitability**. A Ridge model may have statistically significant IC, but if its signals flip position frequently, turnover costs erase the edge. The momentum baseline can beat ML after costs even with lower raw IC.

## Linear Model Meta-Analysis

NB07 compares Ridge/LASSO/Elastic Net across all 9 case studies (ETFs, US equities, crypto, FX, futures). The practical takeaways:

- Ridge is the strongest linear baseline across asset classes
- Low IC asset classes (crypto, FX) challenge linear models — motivating non-linear models (Ch12+)
- IC and net Sharpe ratio are often weakly correlated — turnover is the missing link

## Links

- [[ml-pipeline-trading]]
- [[regularized-regression-trading]]
- [[walk-forward-evaluation]]
- [[information-coefficient]]
- [[evidence-boundary]]

## Sources

- [ch11_README.md](../../raw/articles/chung-khoan/ch11_README.md)
- [ch11_07_case_study_insights.py](../../raw/articles/chung-khoan/ch11_07_case_study_insights.py)
- [ch11_08_ml_backtest_intro.py](../../raw/articles/chung-khoan/ch11_08_ml_backtest_intro.py)
