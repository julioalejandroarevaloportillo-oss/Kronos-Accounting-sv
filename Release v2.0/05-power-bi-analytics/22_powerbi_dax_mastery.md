---
name: kronos-powerbi-dax-mastery
description: Crafts performant, context-aware DAX measures for Time Intelligence, dynamic segmentation, and cumulative fiscal metrics.
version: 1.0.0
category: power-bi-analytics
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📈 SKILL 22: Advanced DAX Measures & Time Intelligence

## 🎯 Purpose
Write optimized, mathematically accurate Data Analysis Expressions (DAX) measures leveraging filter context, row context, and time intelligence.

## 🛠️ Execution Protocol
1. **Never Use Implicit Measures:** Always write explicit DAX measures (`Total Sales = SUM(Fact_Sales[Amount])`), never drag raw columns into visual values.
2. **Standard Time Intelligence Library:**
```dax
-- Year-to-Date (YTD) Revenue
Revenue_YTD = 
CALCULATE(
    [Total_Revenue],
    DATESYTD(Dim_Date[Date])
)

-- Prior Year Comparison
Revenue_PY = 
CALCULATE(
    [Total_Revenue],
    SAMEPERIODLASTYEAR(Dim_Date[Date])
)

-- Year-over-Year Growth ($ and %)
YoY_Growth_$ = [Total_Revenue] - [Revenue_PY]
YoY_Growth_% = DIVIDE([YoY_Growth_$], [Revenue_PY], 0)
```
3. **Filter Context Invariants:** Use `DIVIDE()` to protect against division by zero; use `KEEPFILTERS()` to preserve existing slicer selections.
