---
name: vat-sv-sales-taxpayer-ledger
description: Builds, audits, and balances the official Salvadoran VAT Sales to Taxpayers Ledger (Libro de Ventas a Contribuyentes) for B2B transactions under Tax Code Art. 141.
version: 1.0.0
category: vat-and-monthly-taxes
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 139, 141, 143; Form F-07 Annex 2 Specifications]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📚 SKILL 07: VAT Sales to Taxpayers Ledger (Libro de Ventas a Contribuyentes)

## 🎯 Purpose
Guide AI agents to aggregate, reconcile, and format the **Sales to Taxpayers Ledger (*Libro de Ventas a Contribuyentes*)**, capturing all B2B Tax Credit Vouchers (`DTE-03`), Credit Notes (`DTE-05`), and Debit Notes (`DTE-06`) for Salvadoran tax authorities.

---

## 1. Statutory Column Structure (Art. 141 C.T.)

| Col # | Field Name | Description |
|---|---|---|
| 1 | `correlativo` | Sequential line counter (1, 2, 3...) |
| 2 | `fechaEmision` | Issue date (`YYYY-MM-DD`) |
| 3 | `tipoDocumento` | `03` (CCF), `05` (NC), `06` (ND) |
| 4 | `numeroControl` | Control number or Generation Code (UUID) |
| 5 | `nrcCliente` | Customer's Tax Registration Number (NRC) |
| 6 | `nombreCliente` | Customer's full registered legal name |
| 7 | `ventasExentas` | Exempt sales to taxpayers |
| 8 | `ventasNoSujetas` | Non-subject sales |
| 9 | `ventasGravadasLocales` | Net domestic taxable base (excluding VAT) |
| 10 | `debitoFiscalIva` | 13% VAT Tax Debit ($Col 9 \times 0.13$) |
| 11 | `ivaRetenidoClientes` | 1% Withholding deducted by Large Taxpayer clients |
| 12 | `ivaPercibidoEmpresa` | 1% or 2% Perception collected from clients |
| 13 | `totalVentas` | Total B2B transaction value ($Col 7 + Col 8 + Col 9 + Col 10$) |

---

## 2. Validation & Reconciliation Rules

1. **NRC Integrity:** Every customer in this ledger **must possess an active NRC**. If the customer only has a DUI/NIT without NRC, the transaction belongs in the *Consumer Ledger*, not here.
2. **Debit Fiscal Balance:** 
   $$\sum \text{debitoFiscalIva} = \text{Round}\left(\sum \text{ventasGravadasLocales} \times 0.13, 2\right)$$
   Any cent discrepancy due to item-level rounding must be documented.
3. **Credit Note Offsets:** Credit Notes (`05`) must be entered as **negative values** (or clearly indicated deduction rows) reducing both `ventasGravadasLocales` and `debitoFiscalIva`.
4. **Client Withholding Tracking (Col 11):** Must match corresponding `DTE-07` withholding receipts received from clients. This sum becomes a direct tax credit on line 95 of Form F-07.

---

## 3. End-of-Month Summary Format

```text
======================================================================
SUMMARY: VAT SALES TO TAXPAYERS (VENTAS CONTRIBUYENTES) - Period: YYYY-MM
======================================================================
1. Total Taxable Sales to Taxpayers:        $  XX,XXX.XX
2. Total VAT Tax Debit (Débito Fiscal):     $   X,XXX.XX
3. Total Exempt / Non-Subject Sales:        $     XXX.XX
4. Total 1% Withheld by Clients (Credit):   $     XXX.XX
5. Total Perception Collected:              $     XXX.XX
----------------------------------------------------------------------
TOTAL B2B SALES VOLUME:                     $  XX,XXX.XX
======================================================================
```
