---
title: "Chapter 1: The Process Is Your Edge"
url: "https://github.com/stefan-jansen/machine-learning-for-trading/tree/main/01_process_is_edge"
discovered: 2026-07-05
topic: "Phân tích chứng khoán"
type: github_chapter
---

# Chapter 1: The Process Is Your Edge

The chapter establishes the chapter's central claim: in trading, durable performance depends less on picking a sophisticated model than on maintaining a disciplined research process that can survive changing markets, noisy signals, and real-world frictions.

## Learning Objectives

- Distinguish structural breaks, regimes, data drift, concept drift, and online detection.
- Explain ML4T Workflow as a research-to-production system.
- Define the evidence boundary between exploration and confirmation.
- Describe causal inference and generative AI in a disciplined trading workflow.
- Apply regime thinking, implementability checks, and monitoring logic.

## Sections

### Why Process Discipline Matters
Durable trading performance depends on disciplined process more than sophisticated models.

### Introducing the ML4T Workflow
Research-to-production workflow: point-in-time data, scoping rules, iterative feature/model development, realistic strategy design, deployment discipline, monitoring.

### Causal Inference and Generative AI
Causal inference sharpens mechanisms and assumptions. GenAI expands research and unstructured data processing but creates risks: leakage, hallucination, workflow bloat.

### Market Regimes
Regimes support explanation, robustness checks, and live monitoring. Regimes are risk lens, not reliable timing signal.

### Independent vs Institutional
Independent researchers need self-governance: documentation, checkpoints, explicit stop criteria.

## Notebooks
- factor_regimes.ipynb: GMM on factor returns.
- macro_regimes.ipynb: macro indicators from FRED, validated against S&P 500 volatility/drawdowns.
