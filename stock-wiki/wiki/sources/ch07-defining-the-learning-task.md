---
type: source
format: github-chapter
raw_path: raw/articles/chung-khoan/ch07-defining-the-learning-task-readme.md
ingested: 2026-07-12
---

# Chapter 7: Defining the Learning Task

## Summary

Chương 7 đặt bước "defining the learning task" trước modeling: dữ liệu thị trường sau khi được validated vẫn phải đi qua chẩn đoán chất lượng, preprocessing chỉ fit trên train, xử lý outlier có kỷ luật, missing-data rules minh bạch, label engineering và đánh giá signal trước khi dùng trong chiến lược. Trọng tâm không phải làm dữ liệu "sạch đẹp", mà là tạo input ổn định, audit được, so sánh được và tránh leakage.

Các notebook/script trong chương bao phủ toàn bộ pipeline: data quality diagnostics, preprocessing pipeline, label methods, MFE/MAE, signal evaluation bằng IC/quantile/spread, inference cho IC bằng HAC và block bootstrap, kiểm soát multiple testing/selection bias, sanity checks về cơ chế nhân quả, và vai trò của hệ sinh thái thư viện ML4T.

## Key Takeaways

- Feature research bắt đầu trước model training: dữ liệu, label và protocol đánh giá phải được định nghĩa rõ trước khi tối ưu mô hình.
- Preprocessing cần fit trên training window rồi transform validation/test để giảm leakage và giữ tính audit.
- Label có nhiều dạng: forward return, excess return, volatility-scaled label, quantile/rank label, event/triple-barrier style label; lựa chọn label quyết định bài toán học.
- MFE/MAE dùng để hiểu path của trade sau entry, giúp tách signal có triển vọng khỏi signal thắng-thua ngẫu nhiên.
- Signal evaluation cần tách model diagnostics khỏi signal diagnostics và strategy outcomes, tương thích với [[model-signal-strategy-metrics]].
- IC inference phải xử lý autocorrelation/cross-sectional dependence bằng HAC hoặc block bootstrap; t-stat ngây thơ dễ quá lạc quan.
- Multiple testing và selection bias là rủi ro trung tâm khi thử nhiều feature/label/model; cần FDR, Reality Check, SPA hoặc governance tương tự.
- Causal sanity checks kiểm tra cơ chế hợp lý của feature trước khi đưa vào pipeline nghiên cứu.

## Files Ingested

- [README](../../raw/articles/chung-khoan/ch07-defining-the-learning-task-readme.md)
- [Data quality diagnostics](../../raw/articles/chung-khoan/ch07_01_data_quality_diagnostics.py)
- [Preprocessing pipeline](../../raw/articles/chung-khoan/ch07_02_preprocessing_pipeline.py)
- [Label methods](../../raw/articles/chung-khoan/ch07_03_label_methods.py)
- [MFE/MAE](../../raw/articles/chung-khoan/ch07_04_maximum_favorable_adverse_excursion.py)
- [Signal evaluation](../../raw/articles/chung-khoan/ch07_05_signal_evaluation.py)
- [IC inference](../../raw/articles/chung-khoan/ch07_06_ic_inference.py)
- [Multiple testing](../../raw/articles/chung-khoan/ch07_07_multiple_testing.py)
- [Causal sanity checks](../../raw/articles/chung-khoan/ch07_08_causal_sanity_checks.py)
- [ML4T library ecosystem](../../raw/articles/chung-khoan/ch07_10_ml4t_library_ecosystem.py)
- [Benchmark utilities](../../raw/articles/chung-khoan/ch07_benchmark_utils.py)

## Concepts Mentioned

- [[learning-task-definition]]
- [[data-quality-diagnostics]]
- [[train-only-preprocessing]]
- [[label-engineering]]
- [[mfe-mae-analysis]]
- [[information-coefficient]]
- [[ic-inference]]
- [[multiple-testing-selection-bias]]
- [[causal-sanity-checks]]
- [[ml4t-library-ecosystem]]

## Sources

- [GitHub chapter directory](https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/07_defining_the_learning_task)
