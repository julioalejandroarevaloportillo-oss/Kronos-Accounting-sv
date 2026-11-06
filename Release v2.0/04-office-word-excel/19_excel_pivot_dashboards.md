---
name: kronos-excel-pivot-dashboard-builder
description: Automates multi-dimensional Pivot Table creation, data model summarization, and Excel executive dashboards.
version: 1.0.0
category: office-word-excel
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📊 SKILL 19: Excel Pivot Tables, Aggregations & Dashboard Views

## 🎯 Purpose
Transform raw transaction tables into multi-dimensional Pivot Tables, summary KPI scorecards, and interactive dashboard views.

## 🛠️ Execution Protocol
1. **Source Table Sanitation:**
   - Enforce contiguous, non-empty header rows.
   - Remove blank rows and ensure uniform data types per column.
2. **Aggregations Architecture:**
   - Rows: Categorical dimensions (e.g. `Department`, `Expense Type`, `Month`).
   - Columns: Fiscal periods or sub-categories.
   - Values: Sum, Average, Count with proper number formats.
3. **KPI Scorecard Section:**
   - Create 3 to 4 top-of-sheet metric cards: Total Revenue, Gross Margin, Effective Tax Rate, Cash Balance.
   - Use soft background fills (`#EBF1F5`) and large 18pt bold metrics.
