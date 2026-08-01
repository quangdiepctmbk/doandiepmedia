# 12 — Nguồn MACRO VN: Lãi suất điều hành + Lãi suất NHTM + CPI (kiểm chứng 2026-08-01)

> Bổ sung cho **nhóm 8 (macro)** trong `11-data-sources-matrix.md`.
> Toàn bộ cách lấy đã **test thực tế từ VPS** hôm nay.

---

## 1️⃣ Lãi suất điều hành NHNN (tái cấp vốn, chiết khấu) — QUAN TRỌNG NHẤT

### Số liệu hiện hành (kiểm chứng báo chí 2026)
| Chỉ số | Mức | Ghi chú |
|---|---|---|
| **Lãi suất tái cấp vốn** | **4,5%/năm** | UOB + báo chí: "NHNN duy trì ổn định lãi suất tái cấp vốn ở mức 4,5%" |
| Lãi suất chiết khấu | ~3,5%/năm | Tham khảo |
| Chính sách | **Giữ nguyên các mức lãi suất điều hành** | Phó Thống đốc Phạm Thanh Hà, họp báo Chính phủ 04/04/2026 |

### Cách lấy (đã test)
```bash
# 1. SBV (sbv.gov.vn): BỊ CHẶN — trang lãi suất lỗi nội bộ, render JS, curl không lấy được
# 2. dttktt.sbv.gov.vn: CHẶN kết nối từ VPS (port 443 đóng)

# ✅ Google News RSS — HOẠT ĐỘNG từ VPS:
curl -s "https://news.google.com/rss/search?q=%22l%C3%A3i+su%E1%BA%A5t+t%C3%A1i+c%E1%BA%A5p+v%E1%BB%91n%22+NHNN&hl=vi&gl=VN&ceid=VN:vi"
# → lấy title + link bài báo (Laodong, baodautu, Nhadautu...)
# → mở bài qua browser (Google News cần JS để redirect)
```

**Cách vận hành:** lãi suất điều hành đổi **rất ít lần/năm** (chỉ khi NHNN điều chỉnh) → **ghi tay vào file dữ liệu + lưu ngày hiệu lực** là đủ, không cần crawl hàng ngày. Khi có tin NHNN đổi lãi suất → cập nhật 1 dòng.

---

## 2️⃣ Lãi suất NHTM (huy động/cho vay) — repo nghiencuulaisuat

### Nguồn
- **Repo:** https://github.com/Thanhtran-165/nghiencuulaisuat (thư mục `Lai_suat/`)
- **License:** MIT | Cập nhật: 2026-01-19
- **Loại:** Hệ thống scrape lãi suất VN → SQLite → FastAPI + Next.js dashboard

### Lấy được gì
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

### Cách dùng (cho agent)
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

**Kiểm chứng hôm nay (24hmoney trực tiếp):** VCB 2,1/2,4/3,5/3,5/5,9% (1M/3M/6M/12M/24M); MB 4,75/4,75/6,2/6,2/6,6% — 7/7 ngân hàng parse được ✅

---

## 3️⃣ CPI (NSO — GSO đổi tên) — crawl tự động được

### Nguồn
- **NSO:** `https://www.nso.gov.vn/cpi/` (GSO cũ `gso.gov.vn` → redirect về NSO)
- **Số liệu mới nhất (tháng 6/2026):** CPI **MoM -0,39%**, **YoY +4,69%**, tăng 6T đầu năm +3,21%

### Cách crawl (đã test)
```python
import urllib.request, re
UA = {'User-Agent': 'Mozilla/5.0 ... Chrome/120'}

# 1. Lấy danh sách bài công bố CPI hàng tháng
html = urllib.request.urlopen(urllib.request.Request('https://www.nso.gov.vn/cpi/', headers=UA)).read().decode('utf-8','ignore')
titles = re.findall(r'<h3>(.*?)</h3>', html)   # bài mới nhất đứng đầu

# 2. Mở bài mới nhất, trích số liệu
m = re.search(r'href="(https://www.nso.gov.vn/en/data-and-statistics/[^"]*)"', html)
url = m.group(1)
art = urllib.request.urlopen(urllib.request.Request(url, headers=UA)).read().decode('utf-8','ignore')
text = re.sub(r'<[^>]+>', ' ', art)
# "CPI in June increased by 3.21% and rose by 4.69% year-on-year"
# → regex trích MoM / YoY
```

**Ghi chú:** NSO là WordPress → có RSS/liệt kê bài hàng tháng → **crawl hàng tháng** (cron) lưu parquet. Công bố CPI vào ~ngày 6 hàng tháng.

---

## ⚠️ Phân biệt 3 loại lãi suất (KHÔNG nhầm lẫn)

| Loại | Là gì | Nguồn | Tự động? |
|---|---|---|---|
| **Lãi suất điều hành NHNN** | Công cụ chính sách tiền tệ (tái cấp vốn 4,5%) | Google News RSS + báo chí (SBV chặn) | ⚠️ Bán thủ công (đổi hiếm) |
| **Lãi suất NHTM** | Ngân hàng TM niêm yết (VCB 2,1–5,9%) | repo nghiencuulaisuat / 24hmoney | ✅ Crawl được |
| **Lãi suất liên ngân hàng** | Thị trường liên NH | dttktt SBV (chặn) | ⚠️ Khó |

→ **Với backtest VCB:** lãi suất huy động VCB (repo này) phản ánh chi phí vốn ngân hàng → ảnh hưởng NIM. Lãi suất điều hành là công cụ chính sách → ảnh hưởng toàn thị trường. Nếu chỉ lấy 1: **ưu tiên lãi suất điều hành** (feature toàn thị trường).

## Ghi chú vận hành

- Lãi suất điều hành: cập nhật tay khi NHNN công bố (vài lần/năm), lưu `policy_rate.csv` (date, rate)
- Lãi suất NHTM: cron hàng ngày crawl 24hmoney → lưu SQLite/parquet
- CPI: cron hàng tháng crawl NSO → lưu parquet
- Tất cả tuân theo `02-data-standards.md` (raw immutable → standardized)

## Vị trí trong `11-data-sources-matrix.md`

| Nhóm | Chỉ số | Nguồn CHÍNH | Trạng thái |
|---|---|---|---|
| 8 | Lãi suất điều hành NHNN (4,5%) | Google News RSS + báo chí | ⚠️ bán thủ công (đã kiểm chứng) |
| 8 | Lãi suất NHTM (huy động/cho vay) | repo nghiencuulaisuat / 24hmoney | ✅ crawl được (đã test) |
| 8 | CPI YoY/MoM | **NSO** `nso.gov.vn/cpi/` | ✅ crawl được (đã test) |
