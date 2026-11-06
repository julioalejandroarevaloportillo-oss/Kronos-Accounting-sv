---
name: kronos-excel-data-cleaner-reconciliation
description: Ingests, normalizes, deduplicates, and cross-reconciles disparate Excel files using pandas and openpyxl with automated discrepancy logging.
version: 1.0.0
category: office-word-excel
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📊 SKILL 20: Automated Excel Data Sanitation & Reconciliation

## 🎯 Purpose
Clean, deduplicate, re-cast data types, and cross-reconcile multiple conflicting spreadsheets with automated variance reporting.

## 🛠️ Execution Protocol
1. **Sanitation Pipeline:**
   - Strip leading/trailing whitespaces from all text fields.
   - Clean currency strings (`"$1,250.00"` $\rightarrow$ `Decimal("1250.00")`).
   - Standardize dates to ISO-8601 (`YYYY-MM-DD`).
2. **Two-Way Reconciliation (VLOOKUP / Merge):**
   - Perform an outer join between Dataset A (Internal Ledger) and Dataset B (Bank/Vendor Export) on unique keys.
   - Flag: `MATCH`, `EXISTS_IN_A_ONLY`, `EXISTS_IN_B_ONLY`, `AMOUNT_MISMATCH`.
3. **Discrepancy Output Sheet:** Generate an automated "Exceptions & Errors" sheet listing all mismatched rows with delta amounts.
