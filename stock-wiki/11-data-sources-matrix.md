# 11 — Nguồn dữ liệu VN: Tổng hợp & phân vai (đã kiểm chứng 2026-08-01)

> Bảng quyết định cuối: **lấy gì từ nguồn nào** cho 8 nhóm chỉ số của 1 mã chứng khoán.
> Nguyên tắc: vnstock = giá + BCTC; Cafef = dòng vốn (khối ngoại, tự doanh); SBV/GSO = macro.

## Bảng phân vai nguồn dữ liệu

| # | Nhóm chỉ số | Nguồn CHÍNH | Nguồn phụ | Trạng thái |
|---|---|---|---|---|
| 1 | OHLCV + adjClose | **vnstock** `market.equity.ohlcv()` | yfinance `VCB.VN` | ✅ kiểm chứng |
| 2 | Kỹ thuật (RSI, MACD...) | tự tính từ OHLCV | — | ✅ |
| 3 | Định giá (P/E, P/B, EPS) | **vnstock** `fa.equity.ratios()` | Cafef | ✅ |
| 4 | Sinh lời & tăng trưởng | **vnstock** `fa.equity.balance_sheet/income_statement/cash_flow()` | Cafef BCTC | ✅ |
| 5 | Sức khỏe tài chính | **vnstock** BCTC | Cafef | ✅ |
| 6 | NIM/NPL/CAR (bank) | **vnstock** BCTC (tự tính) | Cafef chuyên sâu NH | ⚠️ cần verify |
| 7 | **Khối ngoại theo mã** | **Cafef** `GDKhoiNgoai.ashx` | — | ✅ kiểm chứng |
| 7b | **Tự doanh theo mã** | **Cafef** `GDTuDoanh.ashx` | — | ✅ kiểm chứng |
| 7c | **Room ngoại** | **Cafef** GDKhoiNgoai (`RoomConLai`, `DangSoHuu`) | — | ✅ kiểm chứng |
| 8 | Macro (CPI, lãi suất NHNN) | **NSO** (CPI, crawl được) + **SBV** (lãi suất điều hành, thủ công) + repo nghiencuulaisuat (lãi suất NHTM) | ⚠️ bán tự động |

## Chi tiết endpoint Cafef (đã test thành công)

### GDKhoiNgoai — khối ngoại theo mã
```
GET https://cafef.vn/du-lieu/Ajax/PageNew/DataHistory/GDKhoiNgoai.ashx
    ?Symbol=VCB&Exchange=HOSE&StartDate=06/02/2026&EndDate=07/02/2026&PageIndex=1&PageSize=20
```
Trả: `KLGDRong, GTDGRong, KLMua, GtMua, KLBan, GtBan, RoomConLai, DangSoHuu` + `TradingReport` (VNINDEX). Phân trang bằng `PageIndex`/`PageSize` (max ~50), `TotalCount` cho tổng. Có cho **VCB** ✅

### GDTuDoanh — tự doanh theo mã
```
GET https://cafef.vn/du-lieu/Ajax/PageNew/DataHistory/GDTuDoanh.ashx
    ?Symbol=VCB&Exchange=HOSE&StartDate=06/02/2026&EndDate=07/02/2026&PageIndex=1&PageSize=20
```
Trả: `KLcpMua, KlcpBan, GtMua, GtBan` — **lưu ý lồng trong `Data.ListDataTudoanh`** (khác GDKhoiNgoai là `Data.Data`). Có cho VCB ✅

### GDNN toàn thị trường (dùng ít)
```
GET https://cafef.vn/du-lieu/ajax/pagenew/datagdnn/gdnuocngoai.ashx?TradeCenter=hose&Date=DD/MM/YYYY
```
Trả 224 mã/ngày. **⚠️ THIẾU VCB, TCB, STB, VPB, SHB, OCB** — không dùng cho các mã này; dùng GDKhoiNgoai theo mã thay thế.

## Quy tắc crawl Cafef (quan trọng)

1. Header bắt buộc: `User-Agent: Mozilla/5.0...` + `Referer: https://m.cafef.vn/` (m.cafef.vn redirect về cafef.vn — dùng thẳng cafef.vn)
2. Date format: `DD/MM/YYYY`
3. **Sleep 0.5–1s giữa request** — tránh rate limit/chặn IP
4. Dữ liệu theo ngày → **crawl hàng ngày (cron)** để tích lũy lịch sử
5. Lưu raw immutable → standardized (theo `02-data-standards.md`)

## Macro VN — hướng dẫn thủ công (chưa tự động)

| Chỉ số | Nguồn | Cách lấy |
|---|---|---|
| Lãi suất điều hành NHNN | sbv.gov.vn | Tải công bố định kỳ, nhập tay hoặc parse PDF |
| CPI YoY | gso.gov.vn | Công bố hàng tháng |
| USD/VND | SBV/Vietcombank | vnstock `Retail.exchange_rate()` |
| Giá vàng | vnstock `Retail.gold()` | ✅ |
| PMI | S&P Global | Trả phí/trang tin |

## Kiến trúc data layer đề xuất

```python
# data_loader.py — 1 cửa cho mọi nguồn
from vnstock import Market, Reference, Fundamental

def load_ohlcv(symbol):        # vnstock
    return Market().equity.ohlcv(symbol=symbol, start=..., end=...)

def load_ratios(symbol):       # vnstock
    return Fundamental().equity.ratios(symbol=symbol)

def load_foreign_flow(symbol): # Cafef GDKhoiNgoai
    return crawl_gdkhoingoai(symbol)   # → parquet

def load_proprietary(symbol):  # Cafef GDTuDoanh
    return crawl_gdtudoanh(symbol)     # → parquet

def load_macro(indicator):     # SBV/GSO thủ công
    return read_macro_parquet(indicator)
```

## Kết luận

- **vnstock + Cafef phủ được 7/8 nhóm chỉ số** (chỉ thiếu macro CPI/LS NHNN tự động)
- Cặp **GDKhoiNgoai + GDTuDoanh** của Cafef là mảnh ghép quan trọng nhất còn thiếu — giờ đã có
- Toàn bộ thông số phục vụ đúng 8 nhóm trong `03-feature-library.md`
