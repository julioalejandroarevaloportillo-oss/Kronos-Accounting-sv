---
name: audit-sv-tax-anomaly-detector
description: Automated forensic tax auditor that scans DTEs, ledgers, and tax returns for arithmetic discrepancies, missing withholdings, unauthorized deductions, and tax evasion risks in El Salvador.
version: 1.0.0
category: auditing-and-compliance
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 226-258 (Tax Infractions and Penalties); CVPCPA Audit Standards]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 24: Forensic Tax Anomaly & Discrepancy Detector

## 🎯 Purpose
Empower AI agents to perform automated forensic tax audits on Salvadoran accounting records, detecting regulatory non-compliance, missing withholdings, arithmetic mismatches, and audit risks prior to government scrutiny.

---

## 1. Automated Audit Scan Matrix

The AI auditor checks every transaction against these high-risk triggers:

| Audit Test ID | Risk Area | Detection Rule | Severity |
|---|---|---|:---:|
| **AUD-01** | **Missing 1% Withholding** | Transaction with Large Taxpayer $\ge \$100.00$ without DTE-07 or `ivaRete1` | 🔴 High |
| **AUD-02** | **Omitted 10% Service Withholding** | DTE-14 or professional service CCF paid without 10% ISR deduction (Art. 156) | 🔴 High |
| **AUD-03** | **Expired VAT Credit** | VAT Crédito Fiscal claimed on purchase vouchers older than 3 months | 🔴 High |
| **AUD-04** | **Unbalanced Double Entry** | Journal entry with $|\sum \text{Debit} - \sum \text{Credit}| > \$0.00$ | 🔴 Critical |
| **AUD-05** | **ISSS Ceiling Violation** | Monthly employee ISSS deduction $> \$30.00$ or employer $> \$75.00$ | 🟡 Medium |
| **AUD-06** | **Unrounded VAT Cent Drift** | VAT variance from $\text{Net Base} \times 0.13$ greater than $\pm \$0.01$ | 🟡 Medium |
| **AUD-07** | **Invalid DTE Generation Code** | UUID format not conforming to uppercase RFC-4122 v4 standards | 🔴 High |
| **AUD-08** | **Non-Deductible Invoice** | Missing vendor NRC on B2B CCF claimed as VAT credit | 🔴 Critical |

---

## 2. Audit Report Format

When executing an anomaly scan, the AI must output a structured audit log:

```text
======================================================================
KRONOS AUDIT SCAN REPORT - JURISDICTION: EL SALVADOR
======================================================================
[SUMMARY METRICS]
- Total Documents Audited:        XXX
- Anomaly Count:                  X
- Critical Tax Exposure Found:    $ X,XXX.XX USD

[DETECTED ANOMALIES]
1. [ALERT ID: AUD-01] MISSING 1% VAT WITHHOLDING
   - Voucher: DTE-03-M001P001-000000000000452
   - Vendor: SUMINISTROS INDUSTRIALES S.A. DE C.V. (NRC: 123456-7)
   - Taxable Base: $1,250.00 (Exceeds $100.00 threshold)
   - Issue: Withholding of $12.50 was not deducted.
   - Recommended Remedy: Request or issue DTE-07 Comprobante de Retención immediately.

2. [ALERT ID: AUD-05] ISSS DEDUCTION CEILING EXCEEDED
   - Employee: Carlos Mendoza (Gross Wage: $1,800.00)
   - Calculated ISSS: $54.00 (Calculated at 3% without ceiling cap)
   - Correct Statutory Cap: $30.00 (Max on $1,000.00 wage ceiling)
   - Recommended Remedy: Reimburse employee $24.00 and adjust monthly ISSS planilla.
======================================================================
```
