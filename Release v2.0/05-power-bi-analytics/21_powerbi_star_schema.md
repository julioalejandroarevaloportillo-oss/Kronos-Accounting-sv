---
name: kronos-powerbi-star-schema-architect
description: Designs optimized Star Schema data models (Fact and Dimension tables) in Power BI following Ralph Kimball dimensional modeling best practices.
version: 1.0.0
category: power-bi-analytics
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📈 SKILL 21: Power BI Star Schema Data Modeling (Kimball Architecture)

## 🎯 Purpose
Design high-performance Power BI data models that maximize VertiPaq engine compression and avoid many-to-many relationship traps.

## 🛠️ Execution Protocol
1. **Enforce Star Schema Topology:**
   - **Fact Tables:** Store numeric measures, transactional granularity, and foreign keys (e.g. `Fact_Sales`, `Fact_Expenses`, `Fact_Payroll`).
   - **Dimension Tables:** Store qualitative attributes, filters, and hierarchies (e.g. `Dim_Date`, `Dim_Customer`, `Dim_Account`).
2. **Cardinality & Cross-Filtering:**
   - Always configure **1-to-Many ($1:*$)** relationships from Dimension to Fact.
   - Maintain **Single Direction** cross-filtering; avoid bidirectional cross-filtering unless strictly necessary for security models.
3. **Surrogate Keys & Optimization:**
   - Replace wide text keys with integer surrogate keys.
   - Hide all foreign keys in the Fact table from the report view to force users to filter via Dimensions.
