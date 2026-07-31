# Factor-Based Regime Detection

**Chapter 1 · §1.4 Market Regimes: Change Is the Constant**

**Docker image**: `ml4t`

## Purpose

Demonstrates unsupervised learning for market regime detection using Gaussian Mixture Models (GMM)
on factor returns from the AQR Century of Factor Premia dataset.

## Learning Objectives

- Apply GMM clustering to factor return time series.
- Evaluate cluster count with BIC, AIC, and silhouette scores.
- Visualize regime timelines with historical event annotations.
- Compare factor performance across regimes.

## Book Reference

Section 1.4 of Chapter 1, "Market Regimes: Change Is the Constant" — style-regime view that
precedes the macro-regime view in `macro_regimes.py`.

## Prerequisites

- Familiarity with monthly return series and StandardScaler-style preprocessing.
- Conceptual exposure to mixture models and information criteria.
- AQR Century of Factor Premia parquet at `data/aqr_factors/` (download via
  `uv run python data/factors/aqr_download.py` if missing).

## Background

Inspired by [Two Sigma's 2021 paper](https://www.twosigma.com/articles/a-machine-learning-approach-to-regime-modeling/)
which uses GMM on an 18-factor "Factor Lens" to identify four market regimes. We work with
AQR's longer history (1927+) over Value, Momentum, Carry, and Defensive across multiple asset
classes. There is no objectively "correct" number of regimes; we sweep 2–6 clusters to show
how granularity shapes the regime map.

### Scope: descriptive, not predictive

This notebook fits the GMM and the StandardScaler on the **entire factor-return history**
and then assigns regime labels back over that same history. The result is an *ex-post*
characterization of how the factor space partitions, useful for narrative and for
visualizing where macro events fall within the partitioning. It is **not** a regime
classifier that can be used for prediction: using these labels as features in a trading
strategy would constitute look-ahead because the partition itself was estimated with
future data. Lookahead-safe label construction (walk-forward fitting, point-in-time
information sets, embargoed cross-validation) is introduced from Chapter 6 onward, and
the case-study chapters (Ch16-20) demonstrate how predictive regime features are
constructed and evaluated.

---

## Imports

---

## Configuration

---

## Helper Functions

A small container for GMM fit diagnostics, and a grid-search function
that fits multiple cluster counts and reports BIC, AIC, and silhouette.

---

### Grid Search for Optimal Cluster Count
Fit GMM across multiple cluster counts and evaluate with BIC, AIC, and silhouette.

---

## Load Factor Data

---

## Understanding the Data

The AQR "Century of Factor Premia" dataset contains monthly returns for various factor
strategies across asset classes. Key columns we use:

| Factor | Description |
|--------|-------------|
| **Equity indices Market** | Global developed equity market return (value-weighted) |
| **All asset classes Value** | Cross-asset value factor (long cheap, short expensive) |
| **All asset classes Momentum** | Cross-asset momentum (long top-quantile past returns, short bottom-quantile) |
| **All asset classes Carry** | Cross-asset carry (long high yield, short low yield) |
| **All asset classes Defensive** | Cross-asset low-risk anomaly |

The "Equity indices Market" is what you'd earn investing in a global equity index -
essentially the aggregate return from holding developed market stocks.

---

## Select Factors

---

## Prepare Data for Clustering

---

## Regime Detection with GMM

---

**Interpretation**: BIC is minimised at K=2 (26,170) and silhouette is maximised
at K=2 (0.27); AIC keeps falling out to K=6 (24,930). BIC penalises model complexity
more heavily than AIC, making it the standard choice when the goal is interpretability
rather than maximum likelihood. We proceed with K=2 — a Risk-On / Risk-Off split that
both BIC and silhouette select on this 1927-2024 panel.

The silhouette scores turn negative for K≥4 (−0.02 at K=4, near-zero for K=5 and K=6),
indicating that higher cluster counts produce overlapping, poorly separated regimes.

---

## Model Selection Visualization

The charts below show BIC, AIC, and silhouette scores for different cluster counts.
Note the y-axis is scaled to highlight differences between models.

---

## Regime Timeline Visualization

---

## Two-Regime View: Risk-On vs Risk-Off

The two-regime split separates periods of broad factor outperformance from
periods of broad underperformance. It is the model that BIC and silhouette
select above; the analysis below characterises the two regimes empirically.

---

### Risk-On vs Risk-Off Regime Timeline
Swim lane panel showing regime assignment alongside cumulative equity returns.

---

## Volatility by Regime

A key question: does volatility differ meaningfully between regimes?
If Risk-Off periods have higher volatility, this validates using regime
detection for risk management.

---

### Volatility Regime Chart
Regime bands with rolling volatility, showing how risk environments differ.

---

### Persist Figure 1.5 inputs

The publication-quality version of Figure 1.5 is rendered by
`book/01_process_is_edge/figures/scripts/generate_figure_1_5_factor_regimes_volatility.py`.
That script reads the arrays persisted below so the book build does not
re-fit the GMM.

---

## Factor Behavior by Regime

---

**Interpretation**: The regime split reveals distinct factor behavior:

- **Value is countercyclical**: Returns *increase* during Risk-Off (+5.3% vs +1.6%),
  consistent with the value premium's tendency to compensate for distress risk.
- **Momentum is procyclical**: Much weaker during Risk-Off (+0.4% vs +4.5%),
  reflecting momentum's vulnerability to sharp reversals.
- **Carry and Defensive turn negative** in Risk-Off (−0.6% and −0.5%) — these
  strategies that appear safe in calm markets lose money when conditions deteriorate.
- **Bonds outperform in Risk-Off** (+4.2% vs +0.8%), consistent with the classic
  flight-to-quality effect.

For portfolio construction, this suggests Value and Bonds provide genuine
diversification during stress, while Carry and Defensive do not.

---

## Regime Statistics

Compare key metrics between Risk-On and Risk-Off periods.

---

**Interpretation**: The regime split is stark. Risk-On delivers a Sharpe of 1.11
while Risk-Off drops to 0.12 — equity exposure during Risk-Off is essentially
uncompensated risk. The −76.9% max drawdown in Risk-Off reflects the Great
Depression and underscores that these are not mild corrections.

The direct volatility ratio here (2.2x) is much larger than the rolling-window
average reported earlier (1.3x). The rolling measure smooths over extreme months,
while this calculation captures the full variance within each regime. The direct
measure better reflects what a portfolio actually experiences during Risk-Off.

---

## Regime Duration Analysis

---

**Interpretation**: With 267 transitions over 98 years, the model switches regime
roughly every 4 months on average. Risk-Off episodes are short (avg ~2 months)
— they capture acute stress periods rather than prolonged bear markets. This
choppiness has practical implications: a strategy that reallocates based on these
signals would trade frequently, incurring transaction costs that may erode the
regime-timing benefit. Regime models are more useful for *understanding* market
dynamics than for high-frequency tactical allocation.

---

## Key Takeaways

- **BIC favors two regimes**: K=2 has the lowest BIC and highest silhouette score,
  though AIC prefers more clusters. The two-state model offers the most interpretable
  and stable regime split.
- **Regimes capture distinct risk environments**: Risk-Off has 2.2x higher volatility,
  a Sharpe of 0.12 (vs 1.11), and a max drawdown of −77%.
- **Value is countercyclical**: +5.3% annualized during Risk-Off vs +1.6% during Risk-On.
  Carry and Defensive, despite their names, turn negative in Risk-Off.
- **Momentum is procyclical**: +4.5% during Risk-On vs +0.4% during Risk-Off — weakest
  factor during market stress.
- **Regime signals are noisy**: With transitions every ~4 months on average, this model
  is better suited for understanding factor dynamics than for tactical allocation.

**Next**: `macro_regimes.py` switches from style returns to macro indicators (UNRATE,
DFF, T10Y2Y, CPIAUCSL) and validates the resulting clusters against S&P 500 volatility
and drawdowns. See Chapter 1 §1.4 for the workflow context.
