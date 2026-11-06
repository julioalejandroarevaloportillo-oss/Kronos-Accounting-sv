---
name: kronos-root-cause-analysis-5whys-fishbone
description: Dissects systemic failures, technical bugs, or accounting anomalies using iterative 5-Whys and Ishikawa (Fishbone) causality diagrams.
version: 1.0.0
category: problem-solving
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 🔍 SKILL 06: Root Cause Analysis (5-Whys & Ishikawa Diagrams)

## 🎯 Purpose
Isolate the true underlying failure mechanism of any system or business incident, preventing superficial symptomatic fixes.

## 🛠️ Execution Protocol
1. **Define the Immediate Symptom:** State the defect objectively with empirical evidence (e.g., "$150.00 discrepancy on Form F-07").
2. **Iterative 5-Whys Chain:**
   - *Why 1:* Output tax did not match bank deposit.
   - *Why 2:* A credit note was accounted for as a debit invoice.
   - *Why 3:* The parser did not check `tipoDte == "05"`.
   - *Why 4:* The integration script assumed all incoming XMLs were CCFs.
   - *Why 5:* The ingestion specification lacked a multi-DTE test suite.
3. **Fishbone Categorization (Ishikawa 6Ms):**
   - People, Methods, Machines, Materials, Measurements, Milieu (Environment).
4. **Preventive Action Plan:** Formulate Poka-Yoke (fail-safe) systemic guardrails.
