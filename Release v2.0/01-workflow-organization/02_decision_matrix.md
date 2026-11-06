---
name: kronos-decision-matrix-builder
description: Evaluates competing business, architecture, or software options using weighted multi-criteria decision matrices (MCDA).
version: 1.0.0
category: workflow-organization
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📋 SKILL 02: Multi-Criteria Weighted Decision Matrix

## 🎯 Purpose
Eliminate subjective bias and cognitive drift when choosing between tools, vendors, architectures, or business strategies.

## 🛠️ Execution Protocol
1. **Define Candidate Set:** List mutually exclusive alternatives ($A_1, A_2, \dots, A_n$).
2. **Establish Criteria & Weights:** Define orthogonal dimensions (e.g., Cost, Latency, Scalability, Compliance) normalized so $\sum w_i = 1.0$.
3. **Score Matrix:** Rate each option on a 1-5 or 1-10 scale backed by concrete metrics.
4. **Compute Weighted Score:** $\text{Score}(A_k) = \sum_{i=1}^m w_i \times s_{ki}$.
5. **Sensitivity Analysis:** Check if a $\pm 10\%$ shift in weights flips the winning decision.
