---
name: compliance-sv-f910-f987-reports
description: Prepares, structures, and validates statutory annual and semi-annual informational tax returns for the Salvadoran DGII, specifically Form F-910 (Withholding Annual Report) and Form F-987 (Client and Vendor Transactions Report).
version: 1.0.0
category: auditing-and-compliance
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 120, 123, 124, 125; DGII Resolution on Electronic Informational Reports]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 23: Statutory Informational Reports (F-910, F-987)

## 🎯 Purpose
Instruct AI agents to generate, cross-verify, and format the mandatory informational tax reports required by El Salvador's Ministry of Finance: **Form F-910** (Annual Income Tax Withholdings Report) and **Form F-987** (Report of Operations with Clients, Vendors, Creditors, and Debtors).

---

## 1. Form F-910: Annual Income Tax Withholdings Report

- **Filing Deadline:** Annually by **January 31** covering the entire preceding calendar year.
- **Reporting Scope:** Every individual or company to whom the business paid salaries, fees, independent services, dividends, or non-resident remittances.
- **Required Line-Item Details:**
  1. NIT / DUI of the recipient.
  2. Full legal name.
  3. Total gross compensation paid in the year.
  4. Total social security and pension deducted (for employees).
  5. Total Income Tax withheld (*Renta Retenida*).
  6. Code of transaction type: `01` Salaries, `02` Professional Services (10%), `03` Non-Residents (20%), etc.
- **Reconciliation Check:** The annual sum of withholdings reported in F-910 **must match exactly** the sum of all monthly F-14 payments made throughout the year.

---

## 2. Form F-987: Major Operations Report (Clients & Vendors)

- **Filing Deadline:** Semi-annually or annually as scheduled by DGII.
- **Reporting Scope:** Detailed breakdown of all individual transactions with clients and vendors that exceed statutory monetary thresholds (e.g. operations $\ge \$5,000.00$ or all transactions for Large Taxpayers).
- **Required Line-Item Details:**
  1. Transaction Date.
  2. Voucher Type (DTE Type: `01`, `03`, `05`, `14`).
  3. DTE Generation Code / Control Number.
  4. Taxpayer ID (NIT) and Registration Number (NRC).
  5. Net amount, VAT, and total invoiced.

---

## 3. Agent Error Prevention
Before generating submission files:
- Detect duplicate records by UUID or invoice control number.
- Validate that all reported NITs follow Salvadoran 14-digit format or 9-digit modern unified DUI format.
- Output a cross-checking balance against General Ledger accounts `2107` (Taxes Payable).
