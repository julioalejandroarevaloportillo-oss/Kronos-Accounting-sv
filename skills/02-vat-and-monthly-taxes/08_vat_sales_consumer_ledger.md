---
name: vat-sv-sales-consumer-ledger
description: Automates daily rollups, POS cash-register summaries, and export tracking in the official Salvadoran VAT Sales to Final Consumers Ledger (Libro de Ventas a Consumidor Final).
version: 1.0.0
category: vat-and-monthly-taxes
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 140, 142; Executive Decree 296/2004]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📚 SKILL 08: VAT Sales to Final Consumers Ledger (Libro a Consumidor Final)

## 🎯 Purpose
Instruct AI agents to generate, balance, and maintain the statutory **Sales to Final Consumers Ledger (*Libro de Ventas a Consumidor Final*)**, incorporating Electronic Invoices (`DTE-01`), POS daily register cuts (Z-reports), and Export Invoices (`DTE-11`).

---

## 1. Daily Rollup Mechanics (Art. 142 C.T.)

In contrast to the B2B ledger (which is line-by-line per voucher), retail, e-commerce, and point-of-sale businesses record transactions as a **consolidated daily summary** per branch or authorized cash register:

| Col # | Field Name | Description |
|---|---|---|
| 1 | `fecha` | Transaction date (`YYYY-MM-DD`) |
| 2 | `rangoDocumentos` | Starting and ending voucher range (e.g. `DTE-01-001` to `050`) |
| 3 | `ventasExentas` | Exempt sales to end consumers |
| 4 | `ventasNoSujetas` | Non-subject sales |
| 5 | `ventasGravadasLocales` | Net domestic taxable base (back-calculated from gross) |
| 6 | `debitoFiscalIva` | 13% VAT Tax Debit ($Col 5 \times 0.13$) |
| 7 | `ventasExportacion` | Export sales (`DTE-11`) at 0% VAT |
| 8 | `totalVentaDiaria` | Total gross daily sales ($Col 3 + Col 4 + Col 5 + Col 6 + Col 7$) |

---

## 2. Mathematical Extraction of Embedded VAT

Since consumer prices in El Salvador **include the 13% VAT by law**:
1. Take the gross taxable collected total ($G$).
2. Extract the net taxable base ($N$):
   $$N = \text{Round}\left(\frac{G}{1.13}, 2\right)$$
3. Compute the VAT Débito Fiscal ($D$):
   $$D = G - N$$
4. *Check:* Confirm that $N + D = G$ exactly. Never allow a 1-cent discrepancy to remain unallocated.

---

## 3. End-of-Month Consolidation
Aggregate the daily entries into the final monthly total for incorporation into Form F-07:
```text
======================================================================
SUMMARY: VAT SALES TO CONSUMERS (VENTAS CONSUMIDOR FINAL) - YYYY-MM
======================================================================
1. Total Net Taxable Consumer Sales:        $  XX,XXX.XX
2. Total VAT Débito Fiscal (13%):           $   X,XXX.XX
3. Total Export Sales (0% VAT):             $  XX,XXX.XX
4. Total Exempt Sales:                      $     XXX.XX
----------------------------------------------------------------------
TOTAL CONSUMER & EXPORT SALES:              $  XX,XXX.XX
======================================================================
```
