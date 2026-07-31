---
type: source_summary
created: 2026-07-05
updated: 2026-07-05
source: ../../raw/articles/chung-khoan/financial-data-universe.md
url: https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/02_financial_data_universe
---

# Chapter 2: The Financial Data Universe

Chương 2 ML4T cung cấp bản đồ khái niệm trước khi chạm vào bất kỳ dataset nào. Luận điểm cốt lõi: mọi dataset đều nhúng các định nghĩa về timestamp, adjustments, identifiers, revisions — những lựa chọn này quyết định dữ liệu thực sự có nghĩa gì trong nghiên cứu.

## 2.1 Modern Taxonomy

- Market data: giá, khối lượng, order book
- Fundamental data: báo cáo tài chính, chỉ số
- Alternative data: sentiment, satellite, web scraping

## 2.2 Asset-Class Market Data

So sánh "price", "liquidity", "dataset" nghĩa khác nhau giữa equities, ETPs, futures, options, digital assets, FX, fixed income, swaps, commodities.

Các notebooks quan trọng:
- US equities EDA (Wiki Prices, survivorship-bias-free)
- Corporate actions: stock splits, dividends → backward adjustment
- ETFs: 50-ETF universe cho case study
- CME Futures: continuous price series, roll detection, Panama/ratio adjustment
- S&P 500 Options: implied volatility, Greeks (Black-Scholes)
- Crypto perps: funding rate arbitrage, premium index

## 2.3 Data Sourcing Due Diligence

Nguyên nhân research success giả tạo: data defects. Framework gồm:
- Point-in-time correctness
- Survivorship bias
- Corporate action errors
- Identifier mismatches (entity resolution)
- Legal rights, reproducible versioning

Notebooks: data quality framework, point-in-time validation, survivorship bias detection.

## 2.4 Data Storage

So sánh CSV, Parquet, Feather, HDF5, DuckDB, SQLite, TimescaleDB, ClickHouse, QuestDB, PostgreSQL.
- DuckDB + SQLite chạy local
- Pandas vs Polars benchmark (Polars thắng đọc/filter/groupby/join)

## Liên kết

- [[ml4t-workflow]]
- [[machine-learning-for-trading]]
- [[ml4t-library-ecosystem]]
