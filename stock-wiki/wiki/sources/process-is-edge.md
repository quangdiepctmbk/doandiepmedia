---
type: source_summary
created: 2026-07-05
updated: 2026-07-05
source: ../../raw/articles/chung-khoan/process-is-edge.md
url: https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/01_process_is_edge
tags: [trading, process, machine-learning, strategy]
---

# Chapter 1: The Process Is Your Edge

Chương 1 của ML4T nhấn mạnh: trong trading, thành công bền vững phụ thuộc vào **quy trình nghiên cứu kỷ luật** (disciplined research process) hơn là chọn mô hình tinh vi.

## 3 Trụ cột quy trình

1. **Thích nghi thay vì chọn mô hình:** Trading là bài toán thích nghi (adaptation) với thị trường luôn thay đổi, không phải contest chọn model.
2. **Workflow nghiên cứu-đến-triển khai:** Quy trình bao gồm: hạ tầng dữ liệu, scoping, phát triển model, backtest thực tế, deployment và monitoring.
3. **Evidence Boundary (Ranh giới bằng chứng):** Vách ngăn tuyệt đối giữa giai đoạn khám phá (exploration) và xác nhận (confirmation).

## Các khái niệm vận hành

- **Market Regimes:** Xem sự thay đổi thị trường là bài toán rủi ro (risk lens) thay vì tín hiệu timing.
- **Causal Inference:** Dùng để sharpen cơ chế, giả định và chẩn đoán.
- **Generative AI:** Mở rộng nghiên cứu và xử lý dữ liệu thô nhưng cần cảnh giác với leak, hallucination, và workflow bloat.

## Công cụ thực hành

- `factor_regimes.ipynb`: Dùng GMM (Gaussian Mixture Models) để detect regime trên factor returns.
- `macro_regimes.ipynb`: Dùng chỉ báo vĩ mô từ FRED để detect regime.

## Bài học cho nhà nghiên cứu độc lập

Người độc lập phải tự thiết lập governance qua: documentation, checkpoints, và explicit stop criteria. Sự tái sử dụng hạ tầng (reusable infrastructure) là cách tạo lợi thế bền vững.

## Liên kết

- [[evidence-boundary]]
- [[machine-learning-for-trading]]
- [[ml4t-workflow]]
