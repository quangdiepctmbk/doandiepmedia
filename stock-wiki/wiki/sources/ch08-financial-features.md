---
type: source
format: github-chapter
raw_path: raw/articles/chung-khoan/ch08_README.md
ingested: 2026-07-12
---

# Chapter 8: Financial Features

## Summary

Chương 8 dạy quy trình chuyển trading narrative → feature specification có kỷ luật qua 3 bước lọc: horizon alignment, driver hypothesis, role separation. Feature được phân loại thành price-derived features, structural/cross-instrument features, và contextual/slow-moving features.

**Các notebook:**
1. `01_price_volume_features` — trend, reversal, volatility, volume/liquidity, cross-sectional normalization, risk features từ OHLCV
2. `02_microstructure_features` — Kyle Lambda, Amihud illiquidity, OFI, composite liquidity score, flow vs state
3. `03_structural_cross_instrument_features` — carry/term structure, cross-asset relative value (rolling beta, lead-lag, peer z-score), options-implied (IV, skew, variance risk premium)
4. `04_fundamentals_macro_calendar` — SEC XBRL value/quality factors, FRED macro (yield curve, VIX, credit spreads), calendar encodings (sin/cos cyclical, time-to-event), publication-lag handling
5. `05_feature_selection` — IC, correlation filtering, clustering dedup, BH-FDR, stability selection via bootstrap IC, ML feature importance
6. `06_robustness_sensitivity` — parameter sweep/responses surface, near-optimal region, RAS correction, regime-conditional IC, signal×state interactions, implementation variants
7. `07_event_studies` — event generation, market model, AAR/CAAR, event study wrapper, CAR distribution, heatmap
8. `case_study_feature_summary` — cross-case-study inventory, family heatmap, breadth-vs-IC via Fundamental Law

## Key Takeaways

- Feature design có grammar: horizon, driver hypothesis, role separation, reference frame, representation, aggregation.
- Point-in-time correctness là constraint trung tâm cho slow macro/fundamental data.
- Features phân thành signal features, state variables, và context variables.
- Cross-sectional normalization cần làm point-in-time để tránh leakage.
- Flow features (dòng tiền) ≠ state features (trạng thái sổ lệnh).
- Parameter selection dùng response surface + near-optimal region thay vì single best.
- Multiple-testing-aware triage (BH-FDR) cho feature selection.
- Signal×state interactions tạo conditional signals nhưng cần kiểm soát degrees of freedom.

## Files Ingested

- [README](../../raw/articles/chung-khoan/ch08_README.md)
- [Price/volume features](../../raw/articles/chung-khoan/ch08_01_price_volume_features.py)
- [Microstructure features](../../raw/articles/chung-khoan/ch08_02_microstructure_features.py)
- [Structural/cross-instrument features](../../raw/articles/chung-khoan/ch08_03_structural_cross_instrument_features.py)
- [Fundamentals/macro/calendar](../../raw/articles/chung-khoan/ch08_04_fundamentals_macro_calendar.py)
- [Feature selection](../../raw/articles/chung-khoan/ch08_05_feature_selection.py)
- [Robustness/sensitivity](../../raw/articles/chung-khoan/ch08_06_robustness_sensitivity.py)
- [Event studies](../../raw/articles/chung-khoan/ch08_07_event_studies.py)
- [Case study feature summary](../../raw/articles/chung-khoan/ch08_case_study_feature_summary.py)

## Concepts Mentioned

- [[feature-design-grammar]]
- [[price-volume-features]]
- [[microstructure-features]]
- [[structural-cross-instrument-features]]
- [[slow-moving-contextual-features]]
- [[feature-selection-dedup]]
- [[robustness-sensitivity-analysis]]
- [[event-studies]]

## Sources

- [GitHub chapter directory](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/08_financial_features)
