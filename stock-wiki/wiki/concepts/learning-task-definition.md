---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch07-defining-the-learning-task-readme.md]
---

# Learning Task Definition

Learning task definition là bước biến dữ liệu thị trường thành bài toán học cụ thể: chọn horizon, label, feature universe, preprocessing protocol, sampling rule và metric đánh giá trước khi huấn luyện model.

## Definition

Trong Chương 7, defining the learning task là cầu nối giữa [[strategy-research-framework]] và modeling. Nó ép nhà nghiên cứu xác định model học điều gì, tại thời điểm nào, từ dữ liệu nào, và kết quả được đánh giá bằng signal diagnostics nào.

## Why It Matters

Nếu task không rõ, model có thể tối ưu nhầm mục tiêu: dự đoán raw return nhưng strategy cần rank cross-section; dùng label overlap nhưng inference không điều chỉnh autocorrelation; hoặc fit scaler/outlier rule trên toàn bộ sample gây leakage.

## Links

- [[label-engineering]]
- [[train-only-preprocessing]]
- [[model-signal-strategy-metrics]]
- [[strategy-research-framework]]

## Sources

- [Chapter 7 README](../../raw/articles/chung-khoan/ch07-defining-the-learning-task-readme.md)
