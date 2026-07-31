---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07_01_data_quality_diagnostics.py]
---

# Data Quality Diagnostics

Data quality diagnostics là lớp kiểm tra trước preprocessing để phát hiện missingness, stale values, outliers, duplicate records, distribution breaks và các vấn đề có thể làm sai label hoặc feature.

## How It Works

Notebook `01_data_quality_diagnostics.py` mô tả kiểm tra chất lượng dữ liệu như một phần của research protocol, không phải thao tác cosmetic. Chẩn đoán này giúp quyết định dữ liệu nào bị loại, dữ liệu nào được winsorize, và rule nào cần ghi lại để tái lập.

## Practical Use

Trong trading research, diagnostics phải chạy trước [[train-only-preprocessing]] và [[label-engineering]], vì lỗi dữ liệu nhỏ có thể trở thành signal giả hoặc làm IC quá đẹp.

## Links

- [[financial-data-universe]]
- [[train-only-preprocessing]]
- [[learning-task-definition]]

## Sources

- [Data quality diagnostics source](../../raw/articles/chung-khoan/ch07_01_data_quality_diagnostics.py)
