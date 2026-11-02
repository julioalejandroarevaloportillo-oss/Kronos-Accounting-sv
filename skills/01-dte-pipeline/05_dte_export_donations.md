---
name: dte-sv-export-donations
description: Processes and audits Electronic Export Invoices (DTE-11 Factura de Exportación), Donation Vouchers (DTE-15), and Settlement Documents (DTE-08 / DTE-09).
version: 1.0.0
category: dte-pipeline
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 75, 76; Income Tax Law Art. 32; Customs Law]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 05: Export Invoicing, Donations & Special DTEs (DTE-11 / 15 / 08 / 09)

## 🎯 Purpose
Guide AI agents in validating, auditing, and recording specialized Salvadoran DTEs: Export Invoices (`DTE-11`), Donation Receipts (`DTE-15`), Settlement Vouchers (`DTE-08`), and Accounting Settlement Documents (`DTE-09`).

---

## 1. DTE-11: Factura de Exportación (Zero-Rated VAT)

### Core Rules:
- **Zero-Rate VAT (0%):** Under Art. 75 of the Tax Code, exports of goods and services outside El Salvador are taxed at **0%**.
- **Credit Fiscal Recovery:** Exporters retain the legal right to claim and offset VAT Crédito Fiscal paid on local inputs used directly to produce exported goods/services.
- **Foreign Identification:** Receiver ID can be a foreign passport (`tipoDocumento: "03"`), foreign company registry (`tipoDocumento: "37"`), or international tax ID.
- **Incoterms & Customs Info:** Requires Incoterm code (FOB, CIF, EXW), destination country code, and optional Single Customs Declaration (DUCA) reference.

---

## 2. DTE-15: Comprobante de Donación

### Core Rules:
- **Issued By:** Legally recognized non-profit foundations, charities, universities, and government bodies authorized by the Ministry of Finance.
- **Tax Deductibility (Income Tax Law Art. 32):**
  - Deductible for the donor up to **a maximum of 20% of the donor's net taxable income** in the fiscal year.
- **Verification:** The AI must verify the donor's ID and check whether the recipient entity has an active tax-exemption qualification issued by the DGII.

---

## 3. DTE-08 & DTE-09: Settlement Documents

- **DTE-08 (Comprobante de Liquidación):** Used in transactions on behalf of third parties (commissions, consignment sales, auctions).
- **DTE-09 (Documento Contable de Liquidación):** Used by insurance companies, card processors, and regulated clearinghouses to settle balances and charges with affiliated merchants.

---

## 4. Agent Validation Workflow
1. For **DTE-11**: Confirm that no domestic VAT (13%) is added to export items, check currency conversion if billed in EUR or other currency (converted to USD for tax ledger), and record in the *Libro de Ventas a Consumidor Final / Exportaciones* column.
2. For **DTE-15**: Verify non-commercial purpose, zero tax fields, and produce the income tax deduction advisory note.
