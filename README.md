# 🇸🇻 KRONOS: Salvadoran Accounting, Tax & Payroll Automation Suite

[![Model Agnostic](https://img.shields.io/badge/AI-Model--Agnostic-blue.svg)](https://github.com)
[![Jurisdiction](https://img.shields.io/badge/Jurisdiction-El%20Salvador%20%28SV%29-brightgreen.svg)](https://www.mh.gob.sv)
[![Compliance](https://img.shields.io/badge/Compliance-Ministerio%20de%20Hacienda%20%7C%20ISSS%20%7C%20AFP-orange.svg)](https://factura.gob.sv)
[![License](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)

> **Universal AI-native accounting, tax compliance, and payroll automation suite for El Salvador (DTE, VAT, ISSS, AFP, F-07, F-14 & NIIF). Works across Claude, ChatGPT, Gemini, and local LLMs.**

---

## 📖 Overview

**KRONOS** is an open, model-agnostic collection of **25 specialized AI skills** designed to automate the entire fiscal, financial, payroll, and bookkeeping lifecycle under the laws and regulations of **El Salvador**:

- **Ministerio de Hacienda (DGII):** Electronic Invoicing (DTE), VAT Ledgers, Form F-07, Form F-14, Form F-11, F-910, F-987.
- **Labor & Social Security:** ISSS health ceilings, AFP Crecer & Confía pension contributions, Art. 37 Income Tax tables, statutory vacations, aguinaldos, and severance pay.
- **Accounting Standards:** IFRS for SMEs (*NIIF para PYMES*) and the official Chart of Accounts authorized by the **CVPCPA** (*Consejo de Vigilancia de la Profesión de Contaduría Pública y Auditoría*).

---

## 📂 The 25 KRONOS Skills Index

The skills are organized into 5 functional clusters:

### Cluster 01: DTE & E-Invoicing Pipeline (Ministerio de Hacienda)
| File | Skill Name | Description |
|---|---|---|
| [`01_dte_invoice_validator.md`](./skills/01-dte-pipeline/01_dte_invoice_validator.md) | `dte-sv-invoice-parser-validator` | Ingestion, validation, and arithmetic audit of Factura Electrónica (`01`) and Crédito Fiscal (`03` CCF). |
| [`02_dte_credit_debit_notes.md`](./skills/01-dte-pipeline/02_dte_credit_debit_notes.md) | `dte-sv-credit-debit-notes` | Management of Credit Notes (`05`) and Debit Notes (`06`) linked to original DTE generation codes. |
| [`03_dte_withholding_vouchers.md`](./skills/01-dte-pipeline/03_dte_withholding_vouchers.md) | `dte-sv-retention-vouchers` | Electronic Withholding Vouchers (`07`) for 1% VAT Withholding under Tax Code Art. 162. |
| [`04_dte_excluded_subjects.md`](./skills/01-dte-pipeline/04_dte_excluded_subjects.md) | `dte-sv-excluded-subjects` | Invoices for Excluded Subjects (`14`) and 10% Income Tax Withholding under Tax Code Art. 156. |
| [`05_dte_export_donations.md`](./skills/01-dte-pipeline/05_dte_export_donations.md) | `dte-sv-export-donations` | Export Invoices (`11` at 0% VAT), Donation Vouchers (`15`), and Settlement Documents (`08`/`09`). |

### Cluster 02: VAT & Monthly Tax Filing (DGII)
| File | Skill Name | Description |
|---|---|---|
| [`06_vat_purchases_ledger.md`](./skills/02-vat-and-monthly-taxes/06_vat_purchases_ledger.md) | `vat-sv-purchases-ledger` | Official VAT Purchases Ledger (*Libro de Compras*) under Tax Code Art. 141 and F-07 Annex 1. |
| [`07_vat_sales_taxpayer_ledger.md`](./skills/02-vat-and-monthly-taxes/07_vat_sales_taxpayer_ledger.md) | `vat-sv-sales-taxpayer-ledger` | Official B2B Sales Ledger (*Libro de Ventas a Contribuyentes*) and 1% withholding credits. |
| [`08_vat_sales_consumer_ledger.md`](./skills/02-vat-and-monthly-taxes/08_vat_sales_consumer_ledger.md) | `vat-sv-sales-consumer-ledger` | Retail sales daily Z-cut rollup (*Libro de Ventas a Consumidor Final*) and embedded VAT extraction. |
| [`09_tax_form_f07_preparer.md`](./skills/02-vat-and-monthly-taxes/09_tax_form_f07_preparer.md) | `tax-sv-form-f07-preparer` | Monthly VAT Return (*Formulario F-07*), debit/credit netting, and surplus carryover. |
| [`10_tax_advance_f14_preparer.md`](./skills/02-vat-and-monthly-taxes/10_tax_advance_f14_preparer.md) | `tax-sv-advance-income-tax-f14` | Advance Income Tax (*Pago a Cuenta 1.75%*) and Withholding Return (*Formulario F-14*). |

### Cluster 03: Payroll, Labor & Social Welfare
| File | Skill Name | Description |
|---|---|---|
| [`11_payroll_isss_calculator.md`](./skills/03-payroll-and-labor/11_payroll_isss_calculator.md) | `payroll-sv-isss-calculator` | Social Security (ISSS) health contributions: 3% employee (cap \$30) / 7.5% employer (cap \$75). |
| [`12_payroll_pension_afp_sip.md`](./skills/03-payroll-and-labor/12_payroll_pension_afp_sip.md) | `payroll-sv-pension-afp-sip` | Pension System (AFP Crecer / Confía): 7.25% employee / 8.75% employer (16% total contribution). |
| [`13_payroll_income_tax_art37.md`](./skills/03-payroll-and-labor/13_payroll_income_tax_art37.md) | `payroll-sv-income-tax-art37` | Employee personal income tax withholdings using the 4-bracket tables under Art. 37 ISR. |
| [`14_labor_statutory_benefits.md`](./skills/03-payroll-and-labor/14_labor_statutory_benefits.md) | `labor-sv-statutory-benefits` | Statutory benefits: annual vacation (+30% surcharge), Christmas bonus (*Aguinaldo*), and severance. |
| [`15_payroll_oviisss_sepp_export.md`](./skills/03-payroll-and-labor/15_payroll_oviisss_sepp_export.md) | `payroll-sv-oviisss-sepp-export` | Flat-file generator for government and pension filing platforms: OVISSS and SEPP/AFP. |

### Cluster 04: Bookkeeping & NIIF para PYMES
| File | Skill Name | Description |
|---|---|---|
| [`16_accounting_chart_of_accounts.md`](./skills/04-bookkeeping-and-niif/16_accounting_chart_of_accounts.md) | `accounting-sv-standard-chart-of-accounts` | Official CVPCPA chart of accounts: 1 Assets, 2 Liabilities, 3 Equity, 4 Expenses, 5 Closing, 6 Revenues. |
| [`17_accounting_journal_entries.md`](./skills/04-bookkeeping-and-niif/17_accounting_journal_entries.md) | `accounting-sv-automated-journal-entries` | Balanced double-entry journal entries (*Partidas de Diario*) from commercial operations and DTEs. |
| [`18_accounting_bank_reconciliation.md`](./skills/04-bookkeeping-and-niif/18_accounting_bank_reconciliation.md) | `accounting-sv-bank-reconciliation` | Bank reconciliation engine for Banco Agrícola, BAC Credomatic, Cuscatlán, and Davivienda. |
| [`19_accounting_fixed_assets_depr.md`](./skills/04-bookkeeping-and-niif/19_accounting_fixed_assets_depr.md) | `accounting-sv-fixed-assets-depr` | Depreciation schedules under maximum tax rates (Art. 30 ISR) and capital gains (Art. 42). |
| [`20_accounting_closing_statements.md`](./skills/04-bookkeeping-and-niif/20_accounting_closing_statements.md) | `accounting-sv-closing-statements` | Monthly/annual financial statements, 7% statutory Legal Reserve (Art. 123 C.Com), and closing entries. |

### Cluster 05: Auditing, Compliance & Master Orchestrator
| File | Skill Name | Description |
|---|---|---|
| [`21_tax_annual_income_f11.md`](./skills/05-auditing-and-compliance/21_tax_annual_income_f11.md) | `tax-sv-annual-income-f11` | Annual corporate Income Tax return (*Formulario F-11*), fiscal reconciliation, and non-deductibles. |
| [`22_tax_municipal_alcaldias.md`](./skills/05-auditing-and-compliance/22_tax_municipal_alcaldias.md) | `tax-sv-municipal-alcaldias` | Municipal commercial taxes and Sworn Annual Asset Declarations (*Alcaldías Municipales*). |
| [`23_compliance_f910_f987_reports.md`](./skills/05-auditing-and-compliance/23_compliance_f910_f987_reports.md) | `compliance-sv-f910-f987-reports` | Informational annual reports: Form F-910 (Withholding Summary) and Form F-987 (Client/Vendor Operations). |
| [`24_audit_tax_anomaly_detector.md`](./skills/05-auditing-and-compliance/24_audit_tax_anomaly_detector.md) | `audit-sv-tax-anomaly-detector` | Forensic tax auditor that detects arithmetic errors, omitted withholdings, and audit risks. |
| [`25_orchestrator_omni_agent.md`](./skills/05-auditing-and-compliance/25_orchestrator_omni_agent.md) | `orchestrator-sv-omni-accounting-agent` | Master intent classifier and orchestrator routing requests across Skills 01 through 24. |

---

## 🚀 How to Use with Any AI Model

### 1. Anthropic Claude (Claude Desktop / Projects)
- **Claude Projects:** Create a project named *"El Salvador Accounting & Taxes"*, upload the `skills/` folder to **Project Knowledge**, and add `skills/05-auditing-and-compliance/25_orchestrator_omni_agent.md` to **Custom Instructions**.

### 2. OpenAI ChatGPT / Custom GPTs
- **Custom GPT:** Create a new GPT named *"KRONOS Salvadoran Accountant"*. In **Instructions**, paste the content of `25_orchestrator_omni_agent.md`. In **Knowledge**, upload the remaining `.md` files.

### 3. Google Gemini / Antigravity
- Register the skills directly into `.agents/skills/` or invoke them via progressive context disclosure.

### 4. Cursor / Windsurf / Code IDEs
- Add these skills into `.cursor/rules/` to allow your coding agent to write backend code, validations, and database seeds matching Salvadoran fiscal requirements.

### 5. Local LLMs & Agents (Ollama, DeepSeek, CrewAI, LangChain)
- Ingest the markdown files into your agent's system prompt or tool memory store.

---

## ⚖️ Legal & Regulatory Disclaimer
This repository provides automated computational logic, mathematical formulas, and structuring guidelines based on published Salvadoran tax laws and Ministry of Finance technical schemas. Final fiscal filings before the DGII should always be reviewed by a licensed Salvadoran Public Accountant (*Contador Público Autorizado - CPA*).
