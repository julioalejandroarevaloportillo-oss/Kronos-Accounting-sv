---
name: kronos-structured-data-density
description: Mandates Markdown tables, fenced code blocks, and structured JSON over walls of unstructured narrative prose.
version: 1.0.0
category: anti-slop-standards
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 🛡️ SKILL 14: Anti-Slop: Structural Hierarchy & Data Density

## 🎯 Purpose
Replace walls of unreadable narrative text with scannable, structured data containers.

## 🛠️ Execution Protocol
1. **The 3-Sentence Threshold:** If an explanation contains $>3$ parallel items, convert it immediately into a Markdown table, a bulleted list, or a JSON payload.
2. **Explicit Table Schema:**
   - Always label units in headers (e.g., `Amount ($ USD)`, `Latency (ms)`).
   - Right-align numeric columns; left-align text columns.
3. **Fenced Code Blocks:** Always specify syntax highlighting languages (`json`, `python`, `sql`, `dax`, `powershell`).
4. **Callouts for Critical Invariants:** Use GitHub-style alerts (`> [!IMPORTANT]`, `> [!WARNING]`) sparingly for genuine operational risks.
