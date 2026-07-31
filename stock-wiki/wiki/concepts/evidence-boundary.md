---
type: concept
domain: finance
created: 2026-07-05
updated: 2026-07-05
sources: [bao-cao-phan-tich-chuyen-sau-ml-trading-2026]
---

# Evidence Boundary (Ranh giới Bằng chứng)

Khái niệm trung tâm của [[machine-learning-for-trading]]. Tạo vách ngăn giữa giai đoạn khám phá (exploration/tuning) và xác nhận (confirmation/evaluation).

## Định nghĩa

Mọi tín hiệu chỉ hoạt động trong cấu hình hẹp hoặc suy giảm khi thay đổi tham số nhỏ đều phải ở lại giai đoạn khám phá. Không cho phép dùng kết quả test để quay lại tinh chỉnh mô hình.

## Công cụ kiểm định

- [[deflated-sharpe-ratio]] — điều chỉnh Sharpe theo số lần thử nghiệm
- [[combinatorial-purged-cross-validation]] — chống rò rỉ dữ liệu chuỗi thời gian
- Rademacher Anti-Serum (RAS) — xác suất quá khớp
- Walk-forward validation xuyên suốt

## Liên kết

- [[machine-learning-for-trading]]
- [[phan-tich-chung-khoan]]
