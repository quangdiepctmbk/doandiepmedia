---
type: concept
domain: quantitative-finance
created: 2026-07-25
updated: 2026-07-25
sources: [ch09_11_hmm_regimes.py, ch09_12_wasserstein_regimes.py, ch09_13_regime_as_feature.py, ch09_README.md]
---

# Regime Features

Changing market environments encoded as features — từ transparent threshold rules đến Wasserstein clustering.

## Observable Threshold Baselines

- **VIX threshold**: VIX > 20 → stress regime (simple but effective)
- **200-day MA cross**: price above/below 200d MA → bull/bear

## Hidden Markov Models (HMM)

Forward algorithm: compute P(state_t | obs_1:t) efficiently via dynamic programming.

### Filtered vs Smoothed

- **Filtered** (P(state_t | past)): production-safe — used in walk-forward
- **Smoothed** (P(state_t | all data)): uses future info — **look-ahead bias** (research only)

### EM Estimation Pitfalls

- Multiple random initializations needed (avoid local optima)
- K-means seeded initialization
- BIC for number of states
- **Label switching**: states swap identities across refit windows — prevent bằng anchor ordering (mean vol, low vol → state 0, state 1)

### Markov-Switching AR (Hamilton 1989)

State-dependent AR coefficients — parameters switch between regimes. Dùng 2 states: low-vol expansion / high-vol contraction.

## Wasserstein Regime Clustering (Horvath et al. 2021)

Clusters each time window's **empirical distribution** using optimal transport (Wasserstein distance) thay vì moment features (mean, var, skew).

1. **Stream-lift partition**: sliding windows → empirical measures
2. **Wasserstein distance**: cost to transport probability mass between distributions
3. **Wasserstein k-means**: centroids = Wasserstein barycenters
4. **Cluster features**: `wasserstein_cluster`, `cluster_distance`, `tail_divergence`

Better at detecting distributional regime changes (shape, tails) that moment-based methods miss.

## Regime as Feature (vs Regime Switching)

**Soft conditioning** beats **hard switching**:
- **Regime-as-feature** (Approach 1): regime probabilities là input features → single model conditioned on regimes
- **Mixture of experts** (Approach 2): separate sub-models per regime, gated by regime → weighted ensemble

Finding: regime-as-feature thường outperforms mixture-of-experts vì:
- Avoids data fragmentation per regime
- Gradients flow through regime weights
- **Transition periods** handled naturally (soft probabilities, not binary switch)

## Sources

- [ch09_11_hmm_regimes.py](../../raw/articles/chung-khoan/ch09_11_hmm_regimes.py)
- [ch09_12_wasserstein_regimes.py](../../raw/articles/chung-khoan/ch09_12_wasserstein_regimes.py)
- [ch09_13_regime_as_feature.py](../../raw/articles/chung-khoan/ch09_13_regime_as_feature.py)
- [[model-based-feature-extraction]]
- [[factor-regimes]]
- [[macro-regimes-full-notebook]]
- [[two-sigma-regime-modeling]]
- [[uncertainty-as-feature]]
