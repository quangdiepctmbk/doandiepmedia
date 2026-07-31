---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_05_feature_selection.py]
---

# Feature Selection and Deduplication

Feature engineering produces nhiều candidates (different lookbacks, transforms, interaction variants). Quá trình giảm xuống tập production-ready.

## Pipeline Steps

1. **IC computation** — Information Coefficient cho từng feature
2. **Correlation filtering** — loại feature có correlation > threshold với feature khác
3. **Clustering & deduplication** — group features within family, chọn representative
4. **BH-FDR multiple testing correction** — kiểm soát false discovery rate
5. **Stability selection via bootstrap IC** — feature ổn định qua resample mới chọn
6. **ML-based feature importance** — dùng tree-based model để rank
7. **Post-selection verification** — out-of-sample IC test

## Links

- [[multiple-testing-selection-bias]]
- [[information-coefficient]]
- [[ic-inference]]
- [[robustness-sensitivity-analysis]]

## Sources

- [Feature selection source](../../raw/articles/chung-khoan/ch08_05_feature_selection.py)
