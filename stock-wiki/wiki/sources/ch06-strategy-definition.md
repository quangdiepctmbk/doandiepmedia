---
type: source
format: chapter
raw_path: raw/articles/chung-khoan/ch06-strategy-definition-readme.md
raw_exploration: raw/articles/chung-khoan/ch06-strategy-definition-exploration.md
raw_code_01: raw/articles/chung-khoan/ch06_01_cv_foundations.py
raw_code_02: raw/articles/chung-khoan/ch06_02_case_study_overview.py
ingested: 2026-07-11
---

# Chương 6: Strategy Research Framework — ML4T

## Tóm tắt

Chương 6 định nghĩa **trading strategy không chỉ là signal hay model, mà là một quy trình ra quyết định có thể thực thi được**, phải được định nghĩa tại thời điểm quyết định và đánh giá như thể nó đang chạy thật. Phân biệt rõ **live trading loop** và **research loop** — hai vòng lặp riêng biệt.

## Nội dung chính

- **§6.1** — ML4T Workflow: phân tách research loop (cải tiến pipeline) và live loop (thực thi cố định)
- **§6.2** — Strategy Map: strategy families (bộ lọc khả thi) × sources of edge (bộ lọc bền vững)
- **§6.3** — Trading Setup: tradability rules, decision schedule, score-to-trade mapping, constraints, costs — tách bạch parameter tuning vs mechanics changes
- **§6.4** — Metrics: 3 cấp độ — model diagnostics, signal diagnostics, strategy outcomes
- **§6.5** — Evaluation Protocol: walk-forward, label buffer (purging), feature buffer (embargo), sealed holdouts, nested walk-forward, CPCV
- **§6.6** — Baseline Checkpoint: narrow baseline như governance tool, sanity checks (timing, coverage, trading intensity)
- **§6.7** — Search Accounting: trial taxonomy (strategy → trial family → trial → run), run logging

## Notebooks

| Notebook | Nội dung | § |
|----------|----------|---|
| `01_cv_foundations` | Walk-forward CV, purging, embargo, calendar-aware splits, CPCV | §6.5 |
| `02_case_study_overview` | 9 case studies (asset classes, universes, cost classes, protocols) | §6.3 |

## Term Sheets (8)

ETF momentum, crypto premium reversal, intraday orderflow reversal, cross-sectional factor momentum, futures carry momentum, FX momentum, options volatility alpha, ETF momentum (legacy)

## References chính

Asness (2013), Bailey & Lopez de Prado (2014, 2015), Bates (2021), Bergmeir (2018), Daniel & Moskowitz (2016), McLean & Pontiff (2016), Moskowitz (2012), Paleologo (2025), Lopez de Prado (2018)

## Links
- [[strategy-research-framework]]
- [[research-loop-vs-live-loop]]
- [[strategy-map-edge]]
- [[trading-setup-definition]]
- [[model-signal-strategy-metrics]]
- [[walk-forward-evaluation]]
- [[baseline-checkpoint]]
- [[trial-taxonomy]]
- [[strategy-term-sheet]]
- [[cv-foundations]]
- [[evidence-boundary]]
- [[backtesting]]
