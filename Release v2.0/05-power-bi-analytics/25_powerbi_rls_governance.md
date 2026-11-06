---
name: kronos-powerbi-rls-governance
description: Configures Row-Level Security (RLS), workspace deployment pipelines, data refresh policies, and certified semantic model governance in Power BI.
version: 1.0.0
category: power-bi-analytics
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📈 SKILL 25: Power BI Row-Level Security (RLS) & Governance

## 🎯 Purpose
Implement enterprise security and governance in Power BI, ensuring users only access their authorized data slices based on identity and role.

## 🛠️ Execution Protocol
1. **Dynamic Row-Level Security (RLS):**
   - Bind security roles using `USERPRINCIPALNAME()`.
```dax
-- Dynamic RLS filter on Dim_UserAccess
[UserEmail] = USERPRINCIPALNAME()
```
2. **Semantic Model Certification:**
   - Designate a single Source of Truth dataset labeled **Certified** for self-service reporting.
   - Separate the Semantic Model (`.pbix` with data model only) from thin report files (`.pbix` connected live to Power BI Service).
3. **Scheduled Refresh & Incremental Refresh:**
   - Configure incremental refresh on large fact tables based on `RangeStart` and `RangeEnd` parameters to keep refresh windows $< 5$ minutes.
