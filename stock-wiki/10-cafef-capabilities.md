# Cafef.vn — Khả năng lấy dữ liệu (đã kiểm chứng thực tế 2026-08-01)

> Tài liệu này ghi kết quả **test thật** từ VPS. Cafef bù các nhóm dữ liệu vnstock thiếu:
> **khối ngoại theo mã** + **tự doanh theo mã**. Dùng kết hợp: `vnstock` (giá/BCTC) + `Cafef` (dòng vốn).

## ✅ Endpoint đã kiểm chứng HOẠT ĐỘNG

### 1. GDKhoiNgoai — Giao dịch khối ngoại THEO MÃ (lịch sử từng ngày)

```
GET https://cafef.vn/du-lieu/Ajax/PageNew/DataHistory/GDKhoiNgoai.ashx?Symbol=VCB&Exchange=HOSE&StartDate=06/02/2026&EndDate=07/02/2026&PageIndex=1&PageSize=20
```
(m.cafef.vn redirect về cafef.vn — dùng thẳng cafef.vn)

**Response JSON:**
```json
{"Data": {
  "TotalCount": 65,
  "Index": "VNINDEX",
  "DateIndex": "31/07/2026",
  "TradingReport": {"klMua":..., "klBan":..., "gtMua":..., "gtBan":...},
  "Data": [
    {"Symbol":"VCB", "Ngay":"31/07/2026",
     "KLGDRong":4563500, "GTDGRong":270239740000,
     "KLMua":5484800, "GtMua":324683000000,
     "KLBan":921300, "GtBan":54443260000,
     "RoomConLai":830869413, "DangSoHuu":20.06}
  ]
}}
```

| Trường | Ý nghĩa |
|--------|---------|
| `KLGDRong` / `GTDGRong` | KL/GT giao dịch ròng (mua − bán) của khối ngoại |
| `KLMua` / `GtMua` | KL/GT khối ngoại mua |
| `KLBan` / `GtBan` | KL/GT khối ngoại bán |
| `RoomConLai` | Room nước ngoài còn lại (cổ phiếu) |
| `DangSoHuu` | % sở hữu nước ngoài hiện tại |
| `ThayDoi` | % thay đổi giá ngày đó |
| `TradingReport` | Tổng hợp toàn thị trường (VNINDEX) |

**Ghi chú kiểm chứng:**
- ✅ Có cho **VCB** (khác endpoint GDNN tổng hợp thiếu VCB — endpoint này theo mã nên đủ)
- ✅ Phân trang: `PageIndex=1,2,3...` với `PageSize` (tối đa ~50/trang), dùng `TotalCount` để biết tổng
- ✅ Date format: `DD/MM/YYYY`
- ⚠️ `ThayDoi` trả chuỗi `"59,30 (+4,96%)"` — phải parse nếu cần số
- ⚠️ Rate limit: chưa rõ, nên crawl chậm (sleep 0.5–1s giữa request)

### 2. GDTuDoanh — Giao dịch TỰ DOANH THEO MÃ (lịch sử từng ngày)

```
GET https://cafef.vn/du-lieu/Ajax/PageNew/DataHistory/GDTuDoanh.ashx?Symbol=VCB&Exchange=HOSE&StartDate=06/02/2026&EndDate=07/02/2026&PageIndex=1&PageSize=20
```

**Response JSON** (lưu ý: `Data` lồng thêm `ListDataTudoanh`):
```json
{"Data": {
  "TotalCount": 136, "DateIndex": "31/07/2026", "Index": "VNINDEX",
  "TradingReport": {"TongGtBan":..., "TongGtMua":..., "TongKlBan":..., "TongKlMua":...},
  "Data": {"ListDataTudoanh": [
    {"Symbol":"VCB", "Date":"31/07/2026",
     "KLcpMua":1396400, "KlcpBan":999500,
     "GtMua":82446300000, "GtBan":58663500000}
  ]}
}}
```

| Trường | Ý nghĩa |
|--------|---------|
| `KLcpMua` / `KlcpBan` | KL tự doanh mua/bán |
| `GtMua` / `GtBan` | GT tự doanh mua/bán |
| `TradingReport` | Tổng hợp tự doanh toàn thị trường |

**Ghi chú:**
- ✅ Có cho cả **ACB và VCB**, phân trang như GDKhoiNgoai
- ✅ Cấu trúc lồng `Data.ListDataTudoanh` — khác GDKhoiNgoai (`Data.Data`) — lưu ý khi parse
- ✅ Tự doanh = giao dịch của chính công ty chứng khoán (proprietary) — tín hiệu dòng tiền thông minh

## 📚 Endpoint khác Cafef (đã thấy, chưa test sâu)

| Endpoint/Trang | Dữ liệu |
|---|---|
| `/du-lieu/ajax/pagenew/datagdnn/gdnuocngoai.ashx?TradeCenter=hose&Date=DD/MM/YYYY` | GDNN **toàn thị trường 224 mã/ngày** (⚠️ thiếu VCB, TCB, STB, VPB — dùng GDKhoiNgoai theo mã thay thế) |
| `/du-lieu/lich-su-giao-dich/hose/all-1.chn` | Lịch sử giao dịch |
| `/du-lieu/lai-suat-ngan-hang.chn` | Lãi suất ngân hàng |
| `/du-lieu/gia-vang-hom-nay/trong-nuoc.chn` | Giá vàng |
| `/du-lieu/hang-hoa.chn` | Hàng hóa |
| `/du-lieu/du-lieu-doanh-nghiep.chn` | Dữ liệu doanh nghiệp |

## 🏗️ Khuyến nghị tích hợp vào pipeline

```python
# Pattern đề xuất cho data layer (kết hợp vnstock + cafef)
# 1. OHLCV + BCTC         → vnstock (Market/Reference/Fundamental)
# 2. Khối ngoại theo mã   → Cafef GDKhoiNgoai (crawl lịch sử, lưu parquet)
# 3. Tự doanh theo mã     → Cafef GDTuDoanh (crawl lịch sử, lưu parquet)
# 4. Macro (CPI, LS NHNN) → SBV/GSO (vnstock và cafef đều thiếu)
```

**Lưu ý crawl:** 2 endpoint này là **theo ngày, có phân trang** — cần:
1. Chạy hàng ngày (cron) để tích lũy lịch sử (không lấy được quá khứ xa nếu không lưu)
2. Sleep 0.5–1s giữa request (tránh rate limit / chặn IP)
3. Lưu raw immutable → standardized → features (theo `02-data-standards.md`)
4. Header `User-Agent` + `Referer` (trang m.cafef.vn) để tránh bị chặn

## ✅ Bảng tổng hợp nguồn dữ liệu đầy đủ

| Nhóm chỉ số | vnstock | Cafef | Ghi chú |
|---|---|---|---|
| 1. OHLCV + adjClose | ✅ | ✅ | vnstock là chính |
| 2. Kỹ thuật | ⚠️ tự tính | ⚠️ | tính từ OHLCV |
| 3. Định giá (P/E, P/B) | ✅ ratios() | ✅ | vnstock là chính |
| 4. Sinh lời & tăng trưởng | ✅ BCTC | ✅ BCTC | vnstock là chính |
| 5. Sức khỏe tài chính | ✅ | ✅ | |
| 6. NIM/NPL/CAR | ⚠️ trong BCTC | ✅ chuyên sâu | |
| 7. **Khối ngoại theo mã** | ❌ | ✅ **GDKhoiNgoai** | **Cafef bù** |
| 7b. **Tự doanh theo mã** | ❌ | ✅ **GDTuDoanh** | **Cafef bù** |
| 7c. Room ngoại | ❌ | ✅ RoomConLai, DangSoHuu | **Cafef bù** |
| 8. Macro (CPI, LS) | ❌ | ⚠️ lãi suất NH | cần SBV/GSO cho CPI |
