---
name: kronos-pre-mortem-risk-mitigation
description: Executes prospective hindsight (Pre-Mortem) to anticipate catastrophic project failure modes before initiating execution.
version: 1.0.0
category: problem-solving
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 🔍 SKILL 09: Prospective Hindsight (Pre-Mortem) & Risk Inversion

## 🎯 Purpose
Stress-test architectures, product launches, and operational rollouts by assuming the project has failed catastrophically and working backward.

## 🛠️ Execution Protocol
1. **The Inversion Premise:** *"Fast-forward 6 months. The implementation has completely collapsed, client accounts are frozen, and the company is facing regulatory fines. What happened?"*
2. **Brainstorm Failure Vectors:**
   - Vendor API deprecation or unexpected schema changes.
   - Database deadlocks during month-end payroll spikes.
   - Staff turnover leaving undocumented credentials.
3. **Score by Impact & Probability:** Prioritize vectors where $\text{Risk Score} = \text{Probability} \times \text{Impact}$.
4. **Deploy Preventative Tripwires:** Install automated monitoring, canary deployments, and redundancy hot-swaps.
