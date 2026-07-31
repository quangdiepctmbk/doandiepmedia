---
tags: [concept, synthetic-data, llm, tabular]
---

# LLM-based Tabular Generators

**GReaT** (Generate Realistic Tabular data) — dùng LLM để sinh dữ liệu bảng tài chính hỗn hợp (numerical + categorical).

## Cơ chế

1. **Serialization**: chuyển mỗi hàng (row) thành câu văn bản (VD: "age=35, income=85000, credit_score=720")
2. **Fine-tune**: huấn luyện LLM (distilgpt2) trên các câu đã serialized
3. **Generation**: giải mã autoregressive → deserialize về dạng bảng
4. **Constraint-based postprocessing**: đảm bảo các ràng buộc business (VD: age ≥ 18)

## Ưu điểm

- Xử lý được schema hỗn hợp (numerical + categorical)
- Mô hình hóa được correlations giữa các cột
- Không cần architecture phức tạp

## Rủi ro

- **Invalid rows**: LLM sinh ra cột vô lý
- **Numerical fidelity**: số floating-point không chính xác
- **Privacy leakage**: LLM có thể ghi nhớ và tái tạo bản ghi gốc

## Data sử dụng
`etf_tabular_data`, `etfs`, `from_dir`

[Source: ch05-synthetic-data-readme.md](../raw/articles/chung-khoan/ch05-synthetic-data-readme.md) | [[generative-models-framework]], [[fidelity-utility-privacy]]
