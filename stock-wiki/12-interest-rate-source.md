# 12 — Nguồn lãi suất ngân hàng: repo nghiencuulaisuat (đã đánh giá 2026-08-01)

> Nguồn bổ sung cho **nhóm 8 (macro)**: lãi suất huy động/cho vay NHTM theo ngày.
> Đánh giá từ mã nguồn GitHub — **chưa chạy crawler**, chỉ ghi cách dùng cho agent.

## Nguồn

- **Repo:** https://github.com/Thanhtran-165/nghiencuulaisuat (thư mục `Lai_suat/`)
- **License:** MIT | Cập nhật: 2026-01-19
- **Loại:** Hệ thống scrape lãi suất VN → SQLite → FastAPI + Next.js dashboard

## Lấy được gì

| Nguồn scrape | Loại | Chi tiết |
|---|---|---|
| Timo.vn (`timo_deposit`) | Lãi suất **tiền gửi** | Nhiều kỳ hạn, parse bảng |
| 24hmoney.vn (`24hmoney_deposit`) | Lãi suất **tiền gửi** | **29+ ngân hàng**, tách "tại quầy" vs "trực tuyến" |
| Timo.vn (`timo_loan`) | Lãi suất **cho vay** | Vay tín chấp, khoảng lãi suất |

**Schema (raw layer):**
```sql
observations(id, source_id, bank_id, series_id, term_id,
             rate_min_pct, rate_max_pct, rate_pct, raw_value,
             observed_day, ...)
UNIQUE(source_id, bank_id, series_id, term_id, observed_day)  -- idempotent theo ngày
```
→ Có **lịch sử theo ngày** (`observed_day`), 2 lớp raw/canonical (khớp triết lý raw-immutable của `02-data-standards.md`).

## Cách dùng (cho agent)

```bash
# 1. Clone + cài
git clone https://github.com/Thanhtran-165/nghiencuulaisuat
cd Lai_suat/backend
pip install -r requirements.txt
python -m app.cli init-db

# 2. Crawl dữ liệu
python -m app.cli scrape --all          # hoặc scrape từng nguồn

# 3. Xuất dữ liệu (nếu có export CLI) hoặc đọc trực tiếp SQLite
# data/rates.db → bảng observations

# 4. (Tùy chọn) chạy API
uvicorn app.main:app --port 8001
# GET /latest?series_code=deposit_online&term_months=12
# GET /history?bank_name=VCB&series_code=deposit_online&term_months=12
```

## ⚠️ Quan trọng — phân biệt 2 loại lãi suất

| Loại | Nguồn này có? | Nguồn thay thế |
|---|---|---|
| **Lãi suất NHTM** (huy động/cho vay — VCB, BID...) | ✅ CÓ (repo này) | Cafef `lai-suat-ngan-hang.chn` |
| **Lãi suất điều hành NHNN** (refinancing, OMO, discount) | ❌ KHÔNG | SBV (chặn bot → lấy tay/browser) |

→ Với backtest VCB: **lãi suất huy động VCB** (repo này) phản ánh chi phí vốn của ngân hàng → ảnh hưởng NIM. **Lãi suất điều hành** là công cụ chính sách → ảnh hưởng toàn thị trường. Nếu chỉ lấy 1: ưu tiên lãi suất điều hành (feature toàn thị trường).

## Ghi chú vận hành

- Dữ liệu **không có sẵn trong repo** — phải tự chạy crawler mới có
- Crawler phụ thuộc Timo/24hmoney — đổi cấu trúc là hỏng (repo có monitoring sẵn)
- Nên chạy **cron hàng ngày** để tích lũy lịch sử (giống khối ngoại Cafef)
- Đã có backend FastAPI + migration runner — có thể tái sử dụng

## Vị trí trong `11-data-sources-matrix.md`

| Nhóm | Chỉ số | Nguồn CHÍNH | Trạng thái |
|---|---|---|---|
| 8 | Lãi suất NHTM (huy động/cho vay) | **repo nghiencuulaisuat** (crawl) / Cafef | 📝 tài liệu xong, chưa chạy |
| 8 | Lãi suất điều hành NHNN | SBV (thủ công) | ⚠️ chưa tự động |
| 8 | CPI YoY/MoM | **NSO** `nso.gov.vn/cpi/` | ✅ crawl được (test OK) |
