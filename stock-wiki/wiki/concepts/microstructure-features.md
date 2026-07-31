---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_02_microstructure_features.py]
---

# Microstructure Features

Microstructure features capture market dynamics không thấy được trong daily OHLCV — proxy cho liquidity, information flow và execution quality.

## Feature Categories

- **Trade-Based Liquidity**: Kyle Lambda (price impact slope), Amihud Illiquidity (|return|/dollar-volume)
- **Order Flow Imbalance (OFI)**: imbalance between buyer/seller-initiated trades; alpha features phải lagged (không dùng contemporaneous OFI)
- **Composite Liquidity Score**: tổng hợp từ bid-ask spread, Kyle Lambda, Amihud, depth
- **Cross-Stock Comparison**: relative liquidity decile

## Critical Distinction

Flow features (dòng lệnh, volume, OFI) ≠ state features (bid-ask spread, depth, queue size). Flow có thể là signal trực tiếp; state mô tả môi trường.

## Timing

Alpha features phải lagged — dùng OFI bar t-1 để predict return bar t.

## Links

- [[price-volume-features]]
- [[feature-design-grammar]]
- [[feature-selection-dedup]]

## Sources

- [Microstructure features source](../../raw/articles/chung-khoan/ch08_02_microstructure_features.py)
