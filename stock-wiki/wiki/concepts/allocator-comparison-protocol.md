---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources:
  - raw/articles/chung-khoan/ch17_08_library_comparison.py
  - raw/articles/chung-khoan/ch17_09_allocator_comparison.py
  - raw/articles/chung-khoan/ch17_05_factor_allocation_evidence.py
---

# Allocator Comparison Protocol

Controlled comparison: same forecasts, same backtest rules, same constraints — only allocator differs.

## Components

- **Library Survey** (NB08): Riskfolio-Lib, PyPortfolioOpt, cvxpy, scipy → comparison
- **Capstone** (NB09): allocators on identical data and protocol — simple heuristics often compete with sophisticated optimization
- **Factor Allocation** (NB05): century of factor performance evidence; value/momentum everywhere; crisis alpha; correlations

## Key Lesson

Allocator gains are context-dependent, often modest, easy to overstate once search risk and execution are considered. If a sophisticated allocator cannot reliably beat simple rules, its extra estimation burden is hard to justify.

## Links

- [[portfolio-construction-ml]]
- [[mvo-robust-kelly]]
- [[hierarchical-risk-parity]]
- [[dl-portfolio-allocation]]
- [[ml-backtest-baseline]]
- [[causal-case-study-insights]]

## Sources

- [ch17_08_library_comparison.py](../../raw/articles/chung-khoan/ch17_08_library_comparison.py)
- [ch17_09_allocator_comparison.py](../../raw/articles/chung-khoan/ch17_09_allocator_comparison.py)
- [ch17_05_factor_allocation_evidence.py](../../raw/articles/chung-khoan/ch17_05_factor_allocation_evidence.py)
