---
type: concept
domain: financial-ml
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch12_03_dl_vs_gbm.py]
---

# Deep Learning vs GBMs for Tabular Data

So sánh GBMs với deep learning alternatives: TabPFN (tabular foundation model), TabM (parameter-efficient ensembling), TabR (nearest neighbors), và MLP.

## Findings (Ch12)

- GBMs vẫn là **default** cho tabular financial data
- TabPFN hữu ích khi **dataset rất nhỏ** (pre-trained prior)
- TabM/TabR có thể beat GBMs khi có **temporal shift structure** phức tạp
- Deep tabular models thêm complexity — chỉ nên dùng khi GBM baseline đã chạm ceiling

NB03 walk-forward IC, training time, và early-stopping behavior trên ETF panel.

## Links

- [[gradient-boosting-trading]]
- [[ensemble-foundations-finance]]
- [[ml-pipeline-trading]]
- [[walk-forward-evaluation]]

## Sources

- [ch12_03_dl_vs_gbm.py](../../raw/articles/chung-khoan/ch12_03_dl_vs_gbm.py)
