# Standard Data Pipeline — Chung cho toàn thị trường

Dựa trên Phase 1 được thiết kế riêng cho VCB, cần mở rộng thành **data pipeline chuẩn hóa** để dễ dàng apply cho bất kỳ cổ phiếu nào (ngân hàng, bất động sản, thép, bán lẻ, thủy sản, dầu khí, chứng khoán, công nghệ…).

## Thiết kế kiến trúc

```
data/
├── raw/                    # Giữ nguyên bản gốc
│   ├── ohlcv/              # Giá VCB, VNINDEX, VN30…
│   ├── fundamentals/       # BCTC quarterly — mỗi mã một file
│   ├── macro/              # Dữ liệu vĩ mô gốc
│   └── corporate_actions/  # Cổ tức, chia tách, phát hành
├── standardized/           # Đã chuẩn hóa format
│   ├── ohlcv/
│   ├── fundamentals/
│   └── macro/
├── features/               # Tính toán sẵn
│   ├── price_volume/       # Returns, volatility, kỹ thuật…
│   ├── fundamental/        # Tỷ lệ tài chính, growth…
│   └── risk/               # Beta, vol regime, drawdown…
└── model_ready/            # Merge xong, sẵn sàng train
```

## Phân loại dữ liệu

### 1. Nhóm dữ liệu — chung cho mọi cổ phiếu

| Nhóm | Ví dụ | Mức độ chuẩn hóa |
|------|-------|-----------------|
| **Giá và khối lượng** | OHLCV daily | **Common** — mọi mã đều có |
| **Chỉ số thị trường** | VN-Index, VN30, HNX-Index | **Common** |
| **Chỉ số ngành** | VN-Banks, VN-RealEstate, VN-Steel (nếu có) | **Common** |
| **Khối lượng giao dịch** | Giá trị, volume, % thay đổi | **Common** |
| **Tỷ lệ cơ bản phổ biến** | P/E, P/B, EPS, BVPS, ROE | **Common** (mọi mã niêm yết đều có BCTC) |
| **Dữ liệu vĩ mô** | Lãi suất, CPI, USD/VND | **Common** |
| **Dữ liệu thị trường chung** | NĐTNN ròng, margin, số TK mở mới | **Common** |

### 2. Nhóm đặc thù — tùy ngành

| Ngành | Feature đặc thù | Nguồn |
|-------|----------------|-------|
| **Ngân hàng** | NIM, NPL, CAR, LLR, tín dụng, huy động, lãi suất cho vay | BCTC ngân hàng + SBV |
| **Bất động sản** | Hàng tồn kho, vay nợ/tổng tài sản, tiến độ bán hàng, giá BĐS | BCTC + DKRA, CBRE |
| **Thép** | Giá thép thế giới, giá HRC/CRC, than, công suất | Thế giới (Reuters, S&P Global), VSA |
| **Bán lẻ** | Doanh thu/m², số lượng cửa hàng, biên lợi nhuận gộp | BCTC + GSO |
| **Dầu khí** | Giá dầu Brent, giá gas, LPG, sản lượng | Thế giới (EIA, OPEC) + PVN |
| **Chứng khoán** | Thanh khoản thị trường, cho vay margin, giá trị danh mục đầu tư | HOSE, VSD |
| **Thủy sản** | Giá cá tra/cá ngừ, tỷ giá, chỉ số xuất khẩu | VASEP, GSO |
| **Công nghệ** | Chi phí R&D, headcount, ARPU, monthly active users | BCTC doanh nghiệp |

### 3. Nhóm dữ liệu alternative (optional — thêm dần)

| Loại | Mục đích | Nguồn | Ghi chú |
|------|---------|-------|---------|
| Tin tức/tweet | Sentiment, event detection | Cafef, VnEconomy, ND H | Sentiment theo từng mã |
| Giao dịch NĐTNN ròng | Dòng vốn ngoại | SSI, FiinTrade | Từng mã riêng |
| Room nước ngoài | Hạn chế sở hữu | SSI, FiinTrade | Từng mã |
| Dividend + ex-date | Corporate action | SSI, VSD | Lịch sử trả cổ tức |

## Standard format cho mỗi loại dữ liệu

### OHLCV (common)

```yaml
symbol: VCB  # hoặc BID, CTG, MWG, HPG…
source: cafef
granularity: daily
adjusted: True  # split/cổ tức điều chỉnh
timezone: Asia/Ho_Chi_Minh
last_updated: 2026-07-26
```

Columns: `date, open, high, low, close, volume, adj_factor`

Fundamentals (common):

```yaml
symbol: VCB
source: cafef
granularity: quarterly
fiscal_year_end: 12  # tháng 12
```

Columns: `report_date, publish_date, period, eps, bvps, roe, roa, pe, pb, total_assets, equity, revenue, net_income, ...`

*Quan trọng: phải có cả `publish_date` để không bị forward-looking bias.*

### Macro (common)

```yaml
source: sbv / gso
granularity: monthly / daily
```

Columns: `date, indicator_name, value, unit, source`

Lưu ở dạng **long format** (date, indicator, value) thay vì wide — dễ thêm indicator mới.

## Data loader API — gợi ý

Thay vì viết script riêng từng mã, xây một data loader tập trung:

```python
# Ví dụ giao diện
loader = DataLoader(root="data/")

# Chung — mọi mã đều gọi được
loader.load_ohlcv("VCB")       # OHLCV
loader.load_benchmark()        # VN-Index
loader.load_macro("CPI")       # CPI
loader.load_macro("rate_sbv")  # Lãi suất NHNN

# Đặc thù — riêng nhóm
loader.load_fundamentals("VCB")           # BCTC chung
loader.load_bank_fundamentals("VCB")      # Thêm NIM, NPL, CAR
loader.load_steel_commodity()             # Giá thép
loader.load_brend()                       # Giá dầu

# Merge tự động
df = loader.build_model_matrix(symbols=["VCB", "BID", "CTG"], 
                                features=["price_volume", "fundamental", "macro"])
```

## Danh sách mã cổ phiếu đề xuất — theo ngành

| Nhóm | Mã | Ghi chú |
|------|-----|---------|
| **Ngân hàng (14 banks)** | VCB, BID, CTG, TCB, MBB, ACB, STB, HDB, VPB, SHB, LPB, MSB, OCB, NAB | Đủ cho factor model, PCA, HRP |
| **Bất động sản** | VHM, VRE, KDH, DXG, NLG, PDR, NVL, DIG, CEO | |
| **Thép** | HPG, NKG, HSG | |
| **Bán lẻ** | MWG, PNJ, FRT, DGW | |
| **Dầu khí** | GAS, PLX, PVD, PVS, PVC | |
| **Chứng khoán** | SSI, VND, HCM, VCI, FTS | |
| **Công nghệ** | FPT, CMG | |
| **Thủy sản** | VHC, ANV, IDI, MPC | |
| **Dệt may** | VGT, TCM, MSH | |
| **Hàng không + logistics** | HVN, VJC, GMD, SCS | |
| **Điện + nước** | POW, NT2, PC1, GEG | |
| **Xây dựng + vật liệu** | CTD, HBC, VGC, BMP, DPM, DCM | |
| **Tiêu dùng + thực phẩm** | SAB, BHN, MSN, VNM, KDC | |

## Lộ trình xây dựng

```
Tuần 1: setup folder structure + OHLCV cho 50+ mã (common)
Tuần 2: BCTC cho 50+ mã — basic (EPS, BVPS, ROE, P/E, P/B) + publish_date (common)
Tuần 3: macro (common)
Tuần 4: feature calculation pipeline — price-volume + fundamental (common)
Tuần 5: ngành feature đặc thù — banking first (NIM, NPL, CAR, credit growth)
Tuần 6: ngành feature đặc thù — top 5 ngành theo ưu tiên
Tuần 7: DataLoader API hoàn chỉnh + integration test
Tuần 8: model_ready pipeline — build_model_matrix() works for any symbol

Sau đó mỗi ngành mới: chỉ cần thêm ~1–2 ngày cho feature đặc thù.
```

## Nguyên tắc thiết kế

1. **Common-first** — 80% dữ liệu (OHLCV + basic fundamental + macro) giống nhau mọi mã. Xử lý một lần, dùng cho tất cả.
2. **Ngành là module plug-in** — thêm ngành mới = thêm 1 module, không sửa core.
3. **Publish date là mandatory** — mỗi báo cáo phải có ngày công bố để tránh forward-looking bias.
4. **Raw immutable** — không sửa dữ liệu gốc, chỉ thêm standardized layer.
5. **Long format macro** — dễ thêm indicator mới không cần restructure schema.
