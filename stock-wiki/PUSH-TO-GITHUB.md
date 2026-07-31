# PUSH-TO-GITHUB.md — Hướng dẫn đưa toàn bộ wiki chứng khoán lên GitHub cho Antigravity

> Gói này chứa **toàn bộ llm-wiki kiến thức chứng khoán** (raw sources + wiki pages + kế hoạch VCB/VN30).
> Mục đích: tạo repo GitHub → mở trong **Antigravity** → agent tự đọc `AGENTS.md` và viết code đúng chuẩn ML4T.

---

## Bước 0 — Tạo repo trên GitHub (1 phút)

1. Mở https://github.com/new
2. **Repository name**: `stock-wiki` (hoặc tên anh thích, VD: `chung-khoan-knowledge`)
3. Chọn **Private** (kiến thức là tài sản — khuyên Private; Antigravity mở private repo cần đăng nhập GitHub)
4. **KHÔNG** tick "Add a README" / ".gitignore" / "license" (gói này đã có sẵn)
5. Bấm **Create repository**

## Bước 1 — Push từ máy có gói này (VPS)

```bash
cd /opt/data/stock-wiki-export
git remote add origin https://github.com/<USERNAME>/stock-wiki.git
git push -u origin main
```

> Nếu máy chưa đăng nhập GitHub, git sẽ hỏi username + **Personal Access Token** (không phải mật khẩu).
> Tạo token tại: GitHub → Settings → Developer settings → Personal access tokens → **Tokens (classic)**
> → Generate new token → tick scope **`repo`** → copy token → dán vào chỗ password.

## Bước 2 — Mở trong Antigravity

1. Mở https://antigravity.ai (hoặc app Antigravity)
2. **New Project** → **Import from GitHub** → chọn repo `stock-wiki`
3. Đợi clone xong
4. Antigravity tự đọc `AGENTS.md` ở gốc repo → biết phải nạp kiến thức theo thứ tự

## Bước 3 — Ra lệnh (test)

Thử prompt này để kiểm tra agent hiểu kiến thức:

> "Đọc AGENTS.md và các file 01–07 theo thứ tự. Viết Python script backtest chiến lược
> RSI(14) < 30 → mua, RSI(14) > 70 → bán trên VCB (VCB.VN), dùng yfinance, áp cost model VN
> (phí 0.15% + thuế bán 0.1% + slippage 0.1%), walk-forward validation, báo cáo
> Sharpe, max drawdown, số lệnh, win rate, net vs gross."

Nếu agent trả lời đúng chuẩn (có cost model, net vs gross, không shuffle time series) → thành công.

---

## Cấu trúc gói

```
stock-wiki-export/
├── AGENTS.md          ← Hướng dẫn agent (đọc file nào, 8 ràng buộc bắt buộc)
├── README.md          ← Tổng quan
├── config.example.yaml ← Config mẫu (an toàn để public)
├── raw/               ← 276 file nguồn (immutable, code ML4T gốc)
│   └── articles/chung-khoan/
├── wiki/              ← Kiến thức đã hệ thống hóa
│   ├── chung-khoan/   ← Kế hoạch VCB 8 phase, VN30 pipeline, data standards
│   ├── concepts/      ← 164 concept pages (backtest, DSR, HRP, causal ML...)
│   ├── sources/       ← 30 source summaries
│   └── entities/      ← 2 entity pages
├── CLAUDE.md, FAQ.md, LICENSE, wiki-viewer.html, run-wiki.sh
└── .gitignore         ← Chặn config.yaml + outputs (bảo mật)
```

## Lưu ý bảo mật

- `config.yaml` **KHÔNG được push** (đã chặn trong .gitignore) — nó có thể chứa API key
- Repo Private khuyến nghị — kiến thức ML4T + kế hoạch là tài sản riêng
- Nếu sau này muốn public, kiểm tra kỹ không có secrets

## Nếu muốn cập nhật wiki sau này

```bash
# Chỉnh sửa nội dung trong /opt/data/llm-wiki (bản gốc), rồi:
cd /opt/data/stock-wiki-export
cp -r /opt/data/llm-wiki/raw /opt/data/llm-wiki/wiki .
git add -A && git commit -m "Update wiki" && git push
```
