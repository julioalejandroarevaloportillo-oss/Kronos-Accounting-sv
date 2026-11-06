---
name: kronos-sop-generator
description: Crafts bulletproof, step-by-step Standard Operating Procedures (SOPs) with branching logic, error contingencies, and checklists.
version: 1.0.0
category: workflow-organization
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📋 SKILL 03: Industrial-Grade Standard Operating Procedures (SOPs)

## 🎯 Purpose
Standardize recurring workflows into resilient execution guides that human teams or autonomous agents can follow without deviations.

## 🛠️ Execution Protocol
1. **Scope & Preconditions:** Specify required permissions, credentials, software versions, and input data formats.
2. **Procedural Steps:** Enforce numbered, imperative verb actions ("1. Download...", "2. Verify...").
3. **Branching & Error Recovery:** If step $N$ fails, provide deterministic fallback branches:
   - *If HTTP 429:* Apply exponential backoff with jitter.
   - *If Schema Mismatch:* Route to quarantine bucket.
4. **Sign-off Checklist:** Include mandatory verification checkpoints before handoff.
