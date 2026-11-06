---
name: kronos-powerbi-power-query-m-pipeline
description: Builds robust Power Query (M) ETL ingestion pipelines with query folding, type enforcement, and dynamic parameterization.
version: 1.0.0
category: power-bi-analytics
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📈 SKILL 23: Power Query (M) Data Extraction & Query Folding

## 🎯 Purpose
Construct automated, robust ETL pipelines in Power Query using M code that pushes computation back to the database engine (Query Folding).

## 🛠️ Execution Protocol
1. **Maximize Query Folding:**
   - Place native SQL/database operations (filter rows, select columns, group by) at the very start of the M pipeline.
   - Avoid non-folding steps (e.g. index column creation, custom M functions) until the final stages.
2. **Standard M Pipeline Structure:**
```powerquery
let
    Source = Sql.Database("db-server.kronos.com", "AccountingDB"),
    FactSales_Table = Source{[Schema="dbo",Item="Fact_Sales"]}[Data],
    FilteredRows = Table.SelectRows(FactSales_Table, each [FiscalYear] >= 2024),
    RemovedColumns = Table.SelectColumns(FilteredRows, {"SaleID", "DateKey", "CustomerKey", "Amount", "VAT"}),
    ChangedType = Table.TransformColumnTypes(RemovedColumns,{
        {"SaleID", Int64.Type}, 
        {"DateKey", Int64.Type}, 
        {"CustomerKey", Int64.Type}, 
        {"Amount", Currency.Type}, 
        {"VAT", Currency.Type}
    })
in
    ChangedType
```
3. **Data Type Rigor:** Explicitly set types (`Currency.Type`, `Date.Type`, `Int64.Type`) on every column to avoid runtime coercion errors.
