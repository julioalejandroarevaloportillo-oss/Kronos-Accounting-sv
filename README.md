# 🇸🇻 KRONOS: Universal AI Accounting, Operations & Analytics Suite

[![Version](https://img.shields.io/badge/Version-2.0.0-black.svg)](CHANGELOG.md)
[![Total Skills](https://img.shields.io/badge/Skills-50%20Skills-blueviolet.svg)](README.md)
[![Model Agnostic](https://img.shields.io/badge/AI-Model--Agnostic-blue.svg)](README.md)
[![Jurisdiction](https://img.shields.io/badge/Jurisdiction-El%20Salvador%20%28SV%29-brightgreen.svg)](https://www.mh.gob.sv)
[![Compliance](https://img.shields.io/badge/Compliance-Hacienda%20%7C%20ISSS%20%7C%20AFP%20%7C%20CVPCPA-orange.svg)](https://factura.gob.sv)

> **50 model-agnostic AI skills for Salvadoran accounting (DTE, VAT, ISSS, AFP) and universal operations (project planning, anti-slop, Word/Excel automation, Power BI). Works with Claude, ChatGPT, Gemini, and local LLMs.**

---

## 📖 Overview

**KRONOS** is an open, model-agnostic library of **50 specialized AI skills** organized in two modules:

### Module A — Salvadoran Accounting & Tax Compliance (25 Skills)
Full automation of the fiscal, financial, payroll, and bookkeeping lifecycle under El Salvador law:
- **Ministerio de Hacienda (DGII):** DTE e-invoicing (types 01, 03, 05, 07, 11, 14), VAT Ledgers, Forms F-07, F-14, F-11, F-910, F-987.
- **Labor & Social Security:** ISSS health ceilings, AFP Crecer & Confía pension contributions, Art. 37 Income Tax tables, vacations, aguinaldos, severance, OVISSS & SEPP flat-file exports.
- **Bookkeeping:** IFRS for SMEs (*NIIF para PYMES*) and the official CVPCPA Chart of Accounts with double-entry journal entries, bank reconciliation, and fixed asset depreciation.

### Module B — Universal Operations, Anti-Slop & Document Automation (25 Skills)
Model-agnostic operational and quality standards applicable to any domain or organization:
- **Workflow Organization:** Project decomposition, decision matrices, SOPs, Eisenhower timeboxing, async stakeholder sync.
- **Problem Solving:** 5-Whys root cause analysis, First-Principles reasoning, Cynefin triage, Pre-Mortem risk inversion, TRIZ contradictions.
- **Anti-Slop Standards:** Fluff elimination, anti-hallucination guardrails, active voice enforcement, structured data density, first-time-right production code.
- **Word & Excel Automation:** `python-docx` executive reports, `docxtpl` mail merge, `openpyxl` financial models, Pivot dashboards, cross-file data reconciliation.
- **Power BI Analytics:** Star Schema (Kimball), DAX time intelligence, Power Query M pipelines, executive dashboard UX, Row-Level Security & governance.

---

## 📂 Module A — Salvadoran Accounting Skills (25 Skills)

### Cluster A1: DTE & E-Invoicing Pipeline
| # | File | Skill | Description |
|:---:|---|---|---|
| 01 | [`01_dte_invoice_validator.md`](./skills/01-dte-pipeline/01_dte_invoice_validator.md) | `dte-sv-invoice-parser-validator` | Validation and audit of Factura Electrónica (`01`) and CCF (`03`). |
| 02 | [`02_dte_credit_debit_notes.md`](./skills/01-dte-pipeline/02_dte_credit_debit_notes.md) | `dte-sv-credit-debit-notes` | Credit Notes (`05`) and Debit Notes (`06`) linked to original generation codes. |
| 03 | [`03_dte_withholding_vouchers.md`](./skills/01-dte-pipeline/03_dte_withholding_vouchers.md) | `dte-sv-retention-vouchers` | 1% VAT Withholding Vouchers (`07`) under Tax Code Art. 162. |
| 04 | [`04_dte_excluded_subjects.md`](./skills/01-dte-pipeline/04_dte_excluded_subjects.md) | `dte-sv-excluded-subjects` | Excluded Subject Invoices (`14`) and 10% Income Tax Withholding (Art. 156). |
| 05 | [`05_dte_export_donations.md`](./skills/01-dte-pipeline/05_dte_export_donations.md) | `dte-sv-export-donations` | Export Invoices (`11`, 0% VAT), Donation Vouchers (`15`), and Settlements (`08`/`09`). |

### Cluster A2: VAT & Monthly Tax Filing (DGII)
| # | File | Skill | Description |
|:---:|---|---|---|
| 06 | [`06_vat_purchases_ledger.md`](./skills/02-vat-and-monthly-taxes/06_vat_purchases_ledger.md) | `vat-sv-purchases-ledger` | *Libro de Compras* under Tax Code Art. 141 and F-07 Annex 1. |
| 07 | [`07_vat_sales_taxpayer_ledger.md`](./skills/02-vat-and-monthly-taxes/07_vat_sales_taxpayer_ledger.md) | `vat-sv-sales-taxpayer-ledger` | *Libro de Ventas a Contribuyentes* and 1% withholding credit tracking. |
| 08 | [`08_vat_sales_consumer_ledger.md`](./skills/02-vat-and-monthly-taxes/08_vat_sales_consumer_ledger.md) | `vat-sv-sales-consumer-ledger` | *Libro de Ventas a Consumidor Final* and embedded 13% VAT extraction. |
| 09 | [`09_tax_form_f07_preparer.md`](./skills/02-vat-and-monthly-taxes/09_tax_form_f07_preparer.md) | `tax-sv-form-f07-preparer` | Monthly VAT Return (*Formulario F-07*), debit/credit netting, surplus carryover. |
| 10 | [`10_tax_advance_f14_preparer.md`](./skills/02-vat-and-monthly-taxes/10_tax_advance_f14_preparer.md) | `tax-sv-advance-income-tax-f14` | Advance Income Tax (*Pago a Cuenta 1.75%*) and *Formulario F-14*. |

### Cluster A3: Payroll, Labor & Social Welfare
| # | File | Skill | Description |
|:---:|---|---|---|
| 11 | [`11_payroll_isss_calculator.md`](./skills/03-payroll-and-labor/11_payroll_isss_calculator.md) | `payroll-sv-isss-calculator` | ISSS: 3% employee (cap \$30) / 7.5% employer (cap \$75). |
| 12 | [`12_payroll_pension_afp_sip.md`](./skills/03-payroll-and-labor/12_payroll_pension_afp_sip.md) | `payroll-sv-pension-afp-sip` | AFP Crecer / Confía: 7.25% employee / 8.75% employer (16% total). |
| 13 | [`13_payroll_income_tax_art37.md`](./skills/03-payroll-and-labor/13_payroll_income_tax_art37.md) | `payroll-sv-income-tax-art37` | 4-bracket monthly & bi-weekly withholding tables under Art. 37 ISR. |
| 14 | [`14_labor_statutory_benefits.md`](./skills/03-payroll-and-labor/14_labor_statutory_benefits.md) | `labor-sv-statutory-benefits` | Vacations (+30%), *Aguinaldo* by seniority brackets, and severance pay. |
| 15 | [`15_payroll_oviisss_sepp_export.md`](./skills/03-payroll-and-labor/15_payroll_oviisss_sepp_export.md) | `payroll-sv-oviisss-sepp-export` | Fixed-width flat-file exports for OVISSS (ISSS) and SEPP (AFP). |

### Cluster A4: Bookkeeping & NIIF para PYMES
| # | File | Skill | Description |
|:---:|---|---|---|
| 16 | [`16_accounting_chart_of_accounts.md`](./skills/04-bookkeeping-and-niif/16_accounting_chart_of_accounts.md) | `accounting-sv-chart-of-accounts` | CVPCPA Chart of Accounts: 1 Assets, 2 Liabilities, 3 Equity, 4 Expenses, 6 Revenues. |
| 17 | [`17_accounting_journal_entries.md`](./skills/04-bookkeeping-and-niif/17_accounting_journal_entries.md) | `accounting-sv-journal-entries` | Balanced double-entry *Partidas de Diario* from DTEs, payroll, and tax settlements. |
| 18 | [`18_accounting_bank_reconciliation.md`](./skills/04-bookkeeping-and-niif/18_accounting_bank_reconciliation.md) | `accounting-sv-bank-reconciliation` | Bank reconciliation for Agrícola, BAC, Cuscatlán, and Davivienda statements. |
| 19 | [`19_accounting_fixed_assets_depr.md`](./skills/04-bookkeeping-and-niif/19_accounting_fixed_assets_depr.md) | `accounting-sv-fixed-assets-depr` | Depreciation schedules (Art. 30 ISR max rates) and capital gains (Art. 42). |
| 20 | [`20_accounting_closing_statements.md`](./skills/04-bookkeeping-and-niif/20_accounting_closing_statements.md) | `accounting-sv-closing-statements` | Financial statements, 7% Legal Reserve (Art. 123 C.Com), and year-end closing entries. |

### Cluster A5: Auditing, Compliance & Master Orchestrator
| # | File | Skill | Description |
|:---:|---|---|---|
| 21 | [`21_tax_annual_income_f11.md`](./skills/05-auditing-and-compliance/21_tax_annual_income_f11.md) | `tax-sv-annual-income-f11` | Annual corporate Income Tax return (*F-11*), fiscal reconciliation, non-deductibles. |
| 22 | [`22_tax_municipal_alcaldias.md`](./skills/05-auditing-and-compliance/22_tax_municipal_alcaldias.md) | `tax-sv-municipal-alcaldias` | Municipal taxes and Sworn Annual Asset Declarations (*Alcaldías SV*). |
| 23 | [`23_compliance_f910_f987_reports.md`](./skills/05-auditing-and-compliance/23_compliance_f910_f987_reports.md) | `compliance-sv-f910-f987` | Annual informational reports: F-910 (Withholdings) and F-987 (Client/Vendor Ops). |
| 24 | [`24_audit_tax_anomaly_detector.md`](./skills/05-auditing-and-compliance/24_audit_tax_anomaly_detector.md) | `audit-sv-anomaly-detector` | Forensic tax scanner: arithmetic errors, missing withholdings, audit risk matrix. |
| 25 | [`25_orchestrator_kronos_agent.md`](./skills/05-auditing-and-compliance/25_orchestrator_omni_agent.md) | `orchestrator-kronos-sv` | Master intent classifier routing all requests across Skills 01–24. |

---

## 📂 Module B — Universal Operations Skills (25 Skills)

### Cluster B1: Workflow & Project Organization
| # | File | Skill | Description |
|:---:|---|---|---|
| 01 | [`01_project_decomposition.md`](./skills_kronos_core/01-workflow-organization/01_project_decomposition.md) | `kronos-project-decomposition` | WBS/DAG task decomposition with critical path and binary completion criteria. |
| 02 | [`02_decision_matrix.md`](./skills_kronos_core/01-workflow-organization/02_decision_matrix.md) | `kronos-decision-matrix-builder` | Weighted multi-criteria decision matrices (MCDA) with sensitivity analysis. |
| 03 | [`03_sop_generator.md`](./skills_kronos_core/01-workflow-organization/03_sop_generator.md) | `kronos-sop-generator` | Industrial-grade SOPs with branching logic and error recovery contingencies. |
| 04 | [`04_eisenhower_timeboxing.md`](./skills_kronos_core/01-workflow-organization/04_eisenhower_timeboxing.md) | `kronos-eisenhower-timeboxing` | Eisenhower quadrant filtering and 90-minute deep-work timeboxing with WIP limits. |
| 05 | [`05_async_stakeholder_sync.md`](./skills_kronos_core/01-workflow-organization/05_async_stakeholder_sync.md) | `kronos-async-stakeholder-sync` | Zero-fluff 3P async progress reports (Progress, Plans, Problems) for any audience. |

### Cluster B2: Advanced Problem Solving
| # | File | Skill | Description |
|:---:|---|---|---|
| 06 | [`06_root_cause_5whys_fishbone.md`](./skills_kronos_core/02-problem-solving/06_root_cause_5whys_fishbone.md) | `kronos-root-cause-5whys` | Root cause analysis via iterative 5-Whys and Ishikawa (6M) fishbone diagrams. |
| 07 | [`07_first_principles_reasoning.md`](./skills_kronos_core/02-problem-solving/07_first_principles_reasoning.md) | `kronos-first-principles` | First-principles deconstruction of legacy assumptions and optimal re-synthesis. |
| 08 | [`08_cynefin_triage.md`](./skills_kronos_core/02-problem-solving/08_cynefin_triage.md) | `kronos-cynefin-triage` | Cynefin domain classification (Clear, Complicated, Complex, Chaotic) and response strategy. |
| 09 | [`09_pre_mortem_risk_mitigation.md`](./skills_kronos_core/02-problem-solving/09_pre_mortem_risk_mitigation.md) | `kronos-pre-mortem` | Prospective hindsight failure analysis and preventative tripwire deployment. |
| 10 | [`10_triz_contradictions.md`](./skills_kronos_core/02-problem-solving/10_triz_contradictions.md) | `kronos-triz-contradictions` | TRIZ inventive principles for resolving zero-sum technical and business trade-offs. |

### Cluster B3: Anti-Slop Standards
| # | File | Skill | Description |
|:---:|---|---|---|
| 11 | [`11_fluff_banisher_conciseness.md`](./skills_kronos_core/03-anti-slop-standards/11_fluff_banisher_conciseness.md) | `kronos-fluff-banisher` | Purges sycophancy, throat-clearing, and AI clichés. Max signal-to-noise density. |
| 12 | [`12_fact_grounding_defense.md`](./skills_kronos_core/03-anti-slop-standards/12_fact_grounding_defense.md) | `kronos-fact-grounding` | Anti-hallucination guardrails: verified citations, exact legal/code references. |
| 13 | [`13_active_voice_assertion.md`](./skills_kronos_core/03-anti-slop-standards/13_active_voice_assertion.md) | `kronos-active-voice` | Strips hedging, passive evasion, and apologetic phrasing from all outputs. |
| 14 | [`14_structured_data_density.md`](./skills_kronos_core/03-anti-slop-standards/14_structured_data_density.md) | `kronos-data-density` | Mandates tables, JSON, and fenced code blocks over unstructured prose. |
| 15 | [`15_first_time_right_code.md`](./skills_kronos_core/03-anti-slop-standards/15_first_time_right_code.md) | `kronos-first-time-right-code` | Zero placeholders, full type hints, deterministic error handling, executable output. |

### Cluster B4: Word & Excel Document Automation
| # | File | Skill | Description |
|:---:|---|---|---|
| 16 | [`16_word_docx_generator.md`](./skills_kronos_core/04-office-word-excel/16_word_docx_generator.md) | `kronos-word-docx-generator` | Executive Word reports (`python-docx`) with brand styles, tables, headers & footers. |
| 17 | [`17_word_template_mailmerge.md`](./skills_kronos_core/04-office-word-excel/17_word_template_mailmerge.md) | `kronos-word-mailmerge` | JSON-to-Word template injection via `docxtpl` Jinja2 for contracts and certificates. |
| 18 | [`18_excel_financial_modeling.md`](./skills_kronos_core/04-office-word-excel/18_excel_financial_modeling.md) | `kronos-excel-financial-model` | Excel workbooks (`openpyxl`) with native formulas, number formats, and frozen panes. |
| 19 | [`19_excel_pivot_dashboards.md`](./skills_kronos_core/04-office-word-excel/19_excel_pivot_dashboards.md) | `kronos-excel-pivot-dashboard` | Multi-dimensional Pivot Tables and KPI scorecard sheets. |
| 20 | [`20_excel_data_cleaner.md`](./skills_kronos_core/04-office-word-excel/20_excel_data_cleaner.md) | `kronos-excel-data-cleaner` | Cross-file deduplication, data type normalization, and variance exception reporting. |

### Cluster B5: Power BI Analytics
| # | File | Skill | Description |
|:---:|---|---|---|
| 21 | [`21_powerbi_star_schema.md`](./skills_kronos_core/05-power-bi-analytics/21_powerbi_star_schema.md) | `kronos-powerbi-star-schema` | Kimball Star Schema: Fact & Dimension tables, 1:* cardinality, surrogate keys. |
| 22 | [`22_powerbi_dax_mastery.md`](./skills_kronos_core/05-power-bi-analytics/22_powerbi_dax_mastery.md) | `kronos-powerbi-dax` | DAX measures: YTD, YoY, SAMEPERIODLASTYEAR, DIVIDE, KEEPFILTERS. |
| 23 | [`23_powerbi_powerquery_m.md`](./skills_kronos_core/05-power-bi-analytics/23_powerbi_powerquery_m.md) | `kronos-powerbi-powerquery` | Power Query M ETL pipelines optimized for Query Folding and strict type enforcement. |
| 24 | [`24_powerbi_dashboard_ui.md`](./skills_kronos_core/05-power-bi-analytics/24_powerbi_dashboard_ui.md) | `kronos-powerbi-dashboard-ui` | Executive dashboard UX: 5-second rule, visual hierarchy, anti-chartjunk color palette. |
| 25 | [`25_powerbi_rls_governance.md`](./skills_kronos_core/05-power-bi-analytics/25_powerbi_rls_governance.md) | `kronos-powerbi-rls` | Dynamic RLS with `USERPRINCIPALNAME()`, certified semantic models, incremental refresh. |

---

## 🚀 How to Use with Any AI Model

### 1. Anthropic Claude (Desktop / Projects)
Create a project, upload the relevant `skills/` or `skills_kronos_core/` folders to **Project Knowledge**, and paste `25_orchestrator_kronos_agent.md` into **Custom Instructions**.

### 2. OpenAI ChatGPT / Custom GPTs
Create a GPT named *"KRONOS"*. Add the orchestrator to **Instructions**. Upload remaining `.md` files to **Knowledge**.

### 3. Google Gemini / Antigravity
Register skills in `.agents/skills/` for progressive context disclosure, or reference individual `.md` files directly in the conversation.

### 4. Cursor / Windsurf / Code IDEs
Drop skills into `.cursor/rules/` or `.agents/rules/`. Reference with `@skill_filename.md` to scope the agent to a specific domain.

### 5. Local LLMs & Agent Frameworks (Ollama, CrewAI, LangChain, AutoGen)
Inject `.md` contents into `system_message`, agent `role_definition`, or a vector-search tool memory store.

---

## 📦 Repository Structure

```text
kronos/
├── skills/                          # Module A: Salvadoran Accounting (25 Skills)
│   ├── 01-dte-pipeline/             # DTE e-invoicing (Skills 01–05)
│   ├── 02-vat-and-monthly-taxes/    # VAT & monthly tax forms (Skills 06–10)
│   ├── 03-payroll-and-labor/        # Payroll & labor law (Skills 11–15)
│   ├── 04-bookkeeping-and-niif/     # Bookkeeping & NIIF (Skills 16–20)
│   └── 05-auditing-and-compliance/  # Audit, compliance & orchestrator (Skills 21–25)
│
├── skills_kronos_core/              # Module B: Universal Operations (25 Skills)
│   ├── 01-workflow-organization/    # Project & task management (Skills 01–05)
│   ├── 02-problem-solving/          # Analytical frameworks (Skills 06–10)
│   ├── 03-anti-slop-standards/      # Output quality enforcement (Skills 11–15)
│   ├── 04-office-word-excel/        # Word & Excel automation (Skills 16–20)
│   └── 05-power-bi-analytics/       # Power BI modeling & governance (Skills 21–25)
```

---

## 📋 Changelog

### v2.0.0 — 2026-11-06
- **Added:** Module B — 25 universal operational skills covering workflow organization, problem-solving frameworks, anti-slop standards, Word/Excel document automation, and Power BI analytics.
- **Added:** `demo_agent/kronos_interactive.py` — persistent interactive console with continuous loop, full error handling, and 4-operation menu covering purchase B2B, payroll, excluded subjects, and F-07 liquidation.

### v1.0.0 — 2026-11-01
- **Initial release:** Module A — 25 El Salvador accounting, tax, and payroll skills covering the full fiscal lifecycle from DTE ingestion to annual income tax returns.

---

## ⚖️ Legal & Regulatory Disclaimer
This repository provides computational logic, mathematical formulas, and structuring guidelines based on published Salvadoran tax laws and Ministry of Finance technical schemas. Final fiscal filings must always be reviewed and signed off by a licensed Salvadoran Public Accountant (*Contador Público Autorizado - CPA*).
