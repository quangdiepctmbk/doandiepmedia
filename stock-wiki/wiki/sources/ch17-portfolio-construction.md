---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch17_README.md
ingested: 2026-07-26
related_raw:
  - ch17_01_portfolio_metrics.py
  - ch17_02_mean_variance_optimization.py
  - ch17_03_robust_optimization.py
  - ch17_04_kelly_criterion.py
  - ch17_05_factor_allocation_evidence.py
  - ch17_06_hierarchical_risk_parity.py
  - ch17_07_conformal_position_sizing.py
  - ch17_08_library_comparison.py
  - ch17_09_allocator_comparison.py
  - ch17_11_dl_portfolio_allocation.py
  - ch17_12_vlstm_portfolio.py
  - ch17_13_deepm_regime_robust.py
  - ch17_deepm/ (10 files)
---

# Portfolio Construction — Chương 17 (ML4T)

## Summary

Chương 17 chuyển từ **có tín hiệu sang xây danh mục**: small modeling decisions ở bước allocation có thể amplify weak edge hoặc destroy strong signal. Từ equal-weight → MVO → robust optimization → Kelly → HRP → conformal sizing → DL end-to-end portfolio.

12 notebooks + deepm/ module.

### Sections (8):

1. **17.1 Definition**: expected returns + covariance + constraints + leverage + rebalancing → weights
2. **17.2 Workflow**: allocator term sheet, leakage controls, separation prediction vs sizing
3. **17.3 Metrics**: Sharpe + IR, active share, HHI, risk contributions, leverage stability (NB01)
4. **17.4 Baselines**: EW, inverse vol, vol targeting, score weighting, risk parity — hard to beat
5. **17.5 MVO & Robust**: Markowitz Curse → shrinkage, constraints, robust optimization (NB02-04)
6. **17.6 HRP**: hierarchical clustering + quasi-diagonalization + recursive bisection (NB06)
7. **17.7 Regime-Adaptive**: conformal sizing (NB07), DL portfolio (NB11), VLSTM (NB12), DeePM (NB13)
8. **17.8 Comparison**: controlled protocol, allocator comparison (NB09), cross-case-study (Ch20)

### Key Takeaways

- **Baselines are hard to beat**: 1/N và inverse vol là competitors mạnh
- **MVO fragile**: expected returns noise + covariance inversion → extreme weights → shrinkage bắt buộc
- **HRP**: stability-first, avoids inversion pathologies
- **Regime-adaptive allocators**: continuous adaptation > discrete switching
- **Conformal sizing**: cải thiện Sharpe +5.5% (ETFs), degradation -24.8% (futures)
- **DL end-to-end**: bypass predict-then-optimize, but high estimation burden
- **Capstone**: NB09 — allocators compared on identical data/protocol

## Reference

- Stefan Jansen, ML for Trading (2nd ed.), Ch. 17
- [GitHub](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/17_portfolio_construction)
- [[ch16-strategy-simulation]] (previous chapter)
