---
type: concept
domain: financial-ml
created: 2026-07-12
updated: 2026-07-12
sources: [raw/articles/chung-khoan/ch08_06_robustness_sensitivity.py]
---

# Robustness and Sensitivity Analysis

A robust signal maintains performance across reasonable parameter variations, regimes và implementation choices.

## Techniques

- **Parameter Sweep / Response Surface**: thay đổi one-knob-at-a-time để thấy IC landscape
- **Near-Optimal Region Breadth**: parameter region rộng → robust; nhọn → overfit
- **RAS Correction**: Reality-Adjusted Selection correction cho parameter snooping
- **Regime-Conditional IC**: IC conditional trên regime state
- **Signal × State Interactions**: gating/scaling variants của signal dựa trên state variable
- **Implementation Variants**: different construction rules cho cùng hypothesis

## Key Insight

Practical improvement thường đến từ signal×state interactions — nhưng mỗi interaction multiplication của degrees of freedom → cần discipline.

## Links

- [[feature-selection-dedup]]
- [[walk-forward-evaluation]]
- [[factor-regimes]]
- [[multiple-testing-selection-bias]]

## Sources

- [Robustness/sensitivity source](../../raw/articles/chung-khoan/ch08_06_robustness_sensitivity.py)
