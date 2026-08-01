# AGENTS.md — Hướng dẫn cho AI coding agent (Antigravity, Cursor, Codex, Claude Code...)

Bạn đang làm việc với **kiến thức chứng khoán VN đã được hệ thống hóa**. Đọc các file sau
**theo thứ tự** trước khi viết bất kỳ code nào liên quan tới phân tích chứng khoán:

1. `01-vietnam-market.md` — đặc thù thị trường VN (bắt buộc)
2. `02-data-standards.md` — chuẩn dữ liệu (bắt buộc)
3. `03-feature-library.md` — công thức feature (bắt buộc nếu làm features)
4. `04-modeling-protocol.md` — validation protocol (bắt buộc nếu train model)
5. `05-backtest-protocol.md` — backtest + chi phí (bắt buộc nếu backtest)
6. `06-risk-governance.md` — risk & deploy (khi cần)
7. `07-vcb-plan.md` — kế hoạch 8 phase VCB (khi làm VCB)
8. `10-cafef-capabilities.md` — endpoint Cafef: khối ngoại, tự doanh (khi cần dòng vốn)
9. `11-data-sources-matrix.md` — bảng phân vai nguồn dữ liệu (khi chọn nguồn)
10. `12-interest-rate-source.md` — lãi suất NHTM: repo nghiencuulaisuat (khi cần lãi suất)

## Ràng buộc bắt buộc (KHÔNG được vi phạm)

1. **Point-in-time data**: fundamental/macro chỉ dùng từ `publish_date`, không dùng
   `period_end_date`. Forward-fill từ publish_date. Cấm tuyệt đối look-ahead bias.
2. **Chia train/test theo thời gian, không shuffle ngẫu nhiên.** Dùng walk-forward CV.
3. **Mọi backtest phải có cost model** (phí + spread + slippage). Gross PnL không được
   báo cáo như kết quả cuối cùng.
4. **Multiple-testing correction**: nếu thử N lần, báo cáo DSR (Deflated Sharpe Ratio)
   hoặc tối thiểu ghi nhận số trials.
5. **Báo cáo phải có**: số lệnh, turnover, Sharpe, max drawdown, win rate, so sánh net
   vs gross. Không báo cáo thiếu metric.
6. **Raw data bất biến**: không sửa file dữ liệu gốc, luôn tạo layer processed riêng.
7. **Dữ liệu VN**: dùng đúng nguồn theo `11-data-sources-matrix.md` — vnstock (giá/BCTC),
   Cafef (khối ngoại/tự doanh — endpoint đã kiểm chứng trong `10-cafef-capabilities.md`).
   KHÔNG tự bịa URL/endpoint — kiểm tra bằng curl trước khi dùng.
8. **Số liệu phải validate**: đếm số lệnh, đối chiếu giá đóng cửa, kiểm tra ngày signal.
   Không bao giờ in số "nhìn đẹp" mà chưa kiểm chứng.

## Thứ tự làm việc chuẩn (cho bất kỳ mã nào)

```
1. Data: OHLCV + benchmark + fundamental + macro (nếu có) → chuẩn hóa → feature matrix
2. Validate feature: IC test, FDR, correlation dedup
3. Baseline: OLS/Ridge walk-forward trước, rồi mới GBM/DL
4. Model selection: IC + hit rate + Sharpe, có gate rõ ràng
5. Backtest: trading protocol đầy đủ + cost model → net PnL
6. Risk: drawdown, stress test → quyết định go/no-go
```

## Khi gặp yêu cầu mơ hồ

Hỏi lại để xác định: mã cổ phiếu nào? Horizon nào? Chi phí nào? Nếu không có thông tin,
dùng mặc định trong các file spec (VD: cost VCB = 0.15% phí + 0.05-0.15% spread).

## Lưu ý về thị trường VN

- Sàn HOSE (VCB, BID...), giờ khớp lệnh 9:00–14:45, ATC 14:30–14:45 (giờ VN).
- Phí môi giới ~0.15% (retail), thuế bán 0.1%, không thuế mua, không thuế lợi vốn.
- Dữ liệu free tốt nhất từ VPS: yfinance `VCB.VN`; Cafef (BCTC), SSI iBoard khi cần.
- Lưu ý: VN không có short-selling phổ biến cho retail — strategy long-only thực tế hơn.
