---
name: vat-sv-purchases-ledger
description: Automates consolidation, arithmetic auditing, and formatting of the official Salvadoran VAT Purchases Ledger (Libro de Compras) in accordance with Tax Code Art. 141.
version: 1.0.0
category: vat-and-monthly-taxes
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 139, 141, 145; Form F-07 Annex 1 Specifications]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📚 SKILL 06: Official VAT Purchases Ledger (Libro de Compras)

## 🎯 Purpose
Guide AI agents to aggregate, audit, and generate the statutory **VAT Purchases Ledger (*Libro de Compras*)** for Salvadoran businesses, formatting data for tax compliance and monthly **Form F-07 Annex 1** electronic submissions.

---

## 1. Statutory Column Structure (Art. 141 C.T.)

Each line item represents a verified input voucher. The AI must compute and present:

| Col # | Field Name | Description |
|---|---|---|
| 1 | `correlativo` | Sequential month index (1, 2, 3...) |
| 2 | `fechaEmision` | Issue date (`YYYY-MM-DD`) |
| 3 | `tipoDocumento` | DTE Type (`03` CCF, `05` NC, `06` ND, `14` Excluded Subject, `04` Póliza/DUCA) |
| 4 | `numeroDocumento` | DTE Generation Code or Control Number |
| 5 | `nrcProveedor` | Vendor's Tax Registration Number (NRC) |
| 6 | `nombreProveedor` | Vendor's registered legal entity or trade name |
| 7 | `comprasExentasLocales` | Non-taxed domestic purchases |
| 8 | `comprasExentasImport` | Exempt imported goods or services |
| 9 | `comprasGravadasLocales` | Domestic net taxable purchases (subject to 13% VAT) |
| 10 | `comprasGravadasImport` | Imported net taxable purchases |
| 11 | `creditoFiscalIva` | 13% VAT Tax Credit ($Col 9 + Col 10 \times 0.13$) |
| 12 | `anticipoIva2` | 2% VAT advance payment at customs (if applicable) |
| 13 | `ivaRetenidoTerceros` | 1% VAT withheld to vendors (if company is Large Taxpayer) |
| 14 | `ivaPercibidoSoportado` | 1% or 2% VAT perception billed by vendors/distributors |
| 15 | `comprasSujetosExcluidos` | Purchases recorded via DTE-14 |
| 16 | `totalCompras` | Total voucher payout |

---

## 2. Integrity & Audit Rules

1. **VAT Deductibility Verification:** Under Art. 65 of the Tax Code, Crédito Fiscal is only deductible if the purchase is **strictly necessary for generating taxable income**. Disallow input tax on personal items, penalties, or non-business entertainment.
2. **Date Window Check:** VAT Crédito Fiscal must be claimed within **3 months** from the date of voucher issuance (Art. 64 C.T.). If older than 3 months, warn the user.
3. **Purchases to Excluded Subjects:** Must be isolated in Column 15 and must **not** generate VAT Crédito Fiscal.

---

## 3. End-of-Month Summary Format

The agent must output a consolidated monthly footer:
```text
======================================================================
SUMMARY: VAT PURCHASES LEDGER (LIBRO DE COMPRAS) - Period: YYYY-MM
======================================================================
1. Total Domestic Taxable Purchases:        $  XX,XXX.XX
2. Total Imported Taxable Purchases:        $  XX,XXX.XX
3. Total VAT Tax Credit (Crédito Fiscal):   $   X,XXX.XX
4. Total Exempt & Non-Subject Purchases:    $     XXX.XX
5. Total Purchases from Excluded Subjects:  $     XXX.XX
6. Total 1% Withholding Practiced:          $     XXX.XX
7. Total 1%/2% Perception Borne:            $     XXX.XX
----------------------------------------------------------------------
TOTAL PURCHASES VOLUME:                     $  XX,XXX.XX
======================================================================
```
