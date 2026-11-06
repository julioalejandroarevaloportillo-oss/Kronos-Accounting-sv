---
name: kronos-fact-grounding-hallucination-defense
description: Restricts responses to verified source documents, demanding cryptographic citations, exact quotes, and explicit admission of unknown variables.
version: 1.0.0
category: anti-slop-standards
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 🛡️ SKILL 12: Anti-Slop: Fact Grounding & Anti-Hallucination Guardrails

## 🎯 Purpose
Prevent confabulations, invented statutory articles, fake API endpoints, or fabricated financial numbers.

## 🛠️ Execution Protocol
1. **The Grounding Imperative:**
   - If a fact is not present in the provided context or verified ground truth repository, the agent must state: `"Information not found in context."`
   - Never extrapolate or interpolate numerical values without stating the mathematical assumption.
2. **Exact Legal / Technical Citations:**
   - Cite the exact statutory article (e.g. `Código Tributario Art. 162`), version number, and published decree.
   - For code, quote exact function signatures and validated parameters.
3. **Epistemic Humility:** Disclose confidence intervals when evaluating incomplete datasets.
