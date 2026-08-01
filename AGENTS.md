# AGENTS.md — Hướng dẫn cho AI coding agent (Antigravity, Cursor, Codex, Claude Code...)

Repo này là **trung tâm tri thức phát triển phần mềm chứng khoán VN**, kết hợp 2 nguồn:

```
doandiepmedia/
├── stock-wiki/    ← KIẾN THỨC ML4T (machine-learning-for-trading, 28 chương)
│                    + kế hoạch VCB/VN30, chuẩn dữ liệu, backtest protocol
├── vnstock-guide/ ← HƯỚNG DẪN DỮ LIỆU VN (vnstock-agent-guide của vnstock-hq)
│                    + docs/ setup, data layers, schema, advanced usage
│                    + hướng dẫn cài & dùng thư viện vnstock
└── doandiep.py     (file riêng của chủ repo — KHÔNG sửa khi không được yêu cầu)
```

## ⚡ NGUYÊN TẮC KẾT HỢP 2 NGUỒN (quan trọng nhất)

1. **`vnstock-guide/` = lớp dữ liệu VN** — khi cần *lấy dữ liệu* (giá, BCTC, macro,
   index, khối ngoại...) → đọc `vnstock-guide/AGENTS.md` + `vnstock-guide/docs/vnstock-data/`
   → cài `pip install -U vnstock` → gọi hàm lấy dữ liệu.
2. **`stock-wiki/` = lớp kiến thức & chuẩn** — khi cần *thiết kế hệ thống* (feature
   engineering, validation, backtest, cost model, risk, DSR...) → đọc
   `stock-wiki/AGENTS.md` + các file `stock-wiki/0X-*.md` theo thứ tự.
3. **Luôn dùng cả 2**: dữ liệu lấy qua vnstock, nhưng *cách xử lý* (point-in-time,
   walk-forward, cost model VN, tránh look-ahead bias) tuân theo stock-wiki.

## Khi được yêu cầu làm việc với chứng khoán VN

1. **Đọc trước**: `stock-wiki/AGENTS.md` (8 ràng buộc) → `stock-wiki/01-vietnam-market.md`
   → `stock-wiki/02-data-standards.md`. Sau đó đọc `vnstock-guide/AGENTS.md` để biết
   cách lấy dữ liệu qua vnstock.
2. **Lấy dữ liệu**: dùng `vnstock` (đã cài qua pip) thay vì tự bịa URL/API.
   - `vnstock-guide/docs/vnstock-data/` — tổng quan các lớp dữ liệu
   - `vnstock-guide/docs/vnstock-data/schema/` — schema chi tiết từng hàm
   - `vnstock-guide/docs/vnstock-data/advanced-usage/` — ví dụ dùng cụ thể
3. **Xử lý & validate**: theo `stock-wiki/03-feature-library.md`, `04-modeling-protocol.md`.
4. **Backtest**: theo `stock-wiki/05-backtest-protocol.md` (cost model VN bắt buộc).
5. **Báo cáo**: số lệnh, turnover, Sharpe, max drawdown, win rate, **net vs gross**.

## Ràng buộc bắt buộc (từ stock-wiki, KHÔNG được vi phạm)

1. **Point-in-time**: fundamental/macro chỉ dùng từ `publish_date`, không từ
   `period_end_date`. Cấm tuyệt đối look-ahead bias.
2. **Chia train/test theo thời gian**, walk-forward CV. Cấm shuffle ngẫu nhiên.
3. **Mọi backtest phải có cost model VN** (phí 0.15% + thuế bán 0.1% + slippage).
   Gross PnL không được báo cáo như kết quả cuối.
4. **Multiple-testing correction** (DSR / t-stat ≥ 3.0).
5. **Báo cáo đầy đủ**: số lệnh, turnover, Sharpe, max DD, win rate, net vs gross.
6. **Raw data bất biến** — luôn tạo layer processed riêng.
7. **Dữ liệu VN lấy qua vnstock** (đã kiểm chứng) — không tự bịa URL/endpoint.
8. **Số liệu phải validate** — không in số "nhìn đẹp" chưa kiểm chứng.

## Khi gặp yêu cầu mơ hồ

Hỏi lại: mã nào? Horizon nào? Chi phí nào? Nếu không rõ, dùng mặc định trong spec
(cost VCB = 0.15% phí + 0.05–0.15% spread, walk-forward năm, v.v.).

## Lưu ý

- `stock-wiki/AGENTS.md` và `vnstock-guide/AGENTS.md` là file hướng dẫn của từng thư
  mục — đọc cả 2, nhưng file gốc này (root AGENTS.md) là ưu tiên cao nhất.
- `vnstock-guide/docs/` có cả `setup-and-debug/` (cài đặt, troubleshooting) — đọc khi
  gặp lỗi cài đặt vnstock.
- Thị trường VN: HOSE 9:00–14:45, phí ~0.15%, thuế bán 0.1%, long-only thực tế hơn.
