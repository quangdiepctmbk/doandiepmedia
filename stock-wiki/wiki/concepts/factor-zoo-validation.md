---
type: concept
domain: quantitative-finance
created: 2026-07-26
updated: 2026-07-26
sources: [raw/articles/chung-khoan/ch15_11_factor_zoo_validation.py]
---

# Factor Zoo Validation

Double-selection LASSO (Belloni-Chernozhukov-Hansen 2014; Feng-Giglio-Xiu 2020) tests which factors retain marginal pricing power after controlling for the rest of the zoo.

## How It Works

1. LASSO treatment on controls (select confounders)
2. LASSO outcome on controls (select predictors)
3. Standard OLS of outcome on treatment + union of selected controls
4. Post-double-selection inference on treatment coefficient

## Application

NB11 builds the zoo from PCA factors + managed-portfolio candidates, testing each against a held-out broad-market ETF. Key insight: held-out outcome breaks the tautology that arises when outcome lies in column span of controls.

## Links

- [[causal-ml-trading]]
- [[double-machine-learning]]
- [[causal-validation-refutation]]
- [[feature-selection-dedup]]
- [[latent-factor-models]]

## Sources

- [ch15_11_factor_zoo_validation.py](../../raw/articles/chung-khoan/ch15_11_factor_zoo_validation.py)
