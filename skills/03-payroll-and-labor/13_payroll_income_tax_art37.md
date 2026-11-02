---
name: payroll-sv-income-tax-art37
description: Computes employee personal income tax withholdings using the official 4-bracket statutory withholding tables under Art. 37 of the Salvadoran Income Tax Law.
version: 1.0.0
category: payroll-and-labor
jurisdiction: El Salvador (SV)
regulatory_references: [Income Tax Law Art. 37, 38; Legislative Decree 548/2015]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 👥 SKILL 13: Payroll Income Tax Withholding (Art. 37 ISR)

## 🎯 Purpose
Instruct AI agents to determine the exact **Personal Income Tax Withholding (*Retención de Renta*)** from employee paychecks, applying the official 4-bracket withholding tables for monthly and bi-weekly payment cycles.

---

## 1. Statutory Net Taxable Base

Income tax is **NEVER** calculated on the gross salary. First, deduct social security and pension employee contributions:
$$\text{Net Taxable Base} = \text{Gross Salary} - \text{ISSS Laboral} - \text{AFP Laboral}$$

---

## 2. Official Monthly Withholding Table (Art. 37 ISR)

| Bracket | From (\$) | To (\$) | Rate | Excess Over (\$) | Fixed Fee (\$) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **I** | \$0.01 | \$472.00 | **Exempt (0%)** | \$0.00 | \$0.00 |
| **II** | \$472.01 | \$895.24 | **10%** | \$472.00 | \$17.67 |
| **III** | \$895.25 | \$2,038.10 | **20%** | \$895.24 | \$60.00 |
| **IV** | \$2,038.11 | And above | **30%** | \$2,038.10 | \$288.57 |

---

## 3. Official Bi-Weekly Withholding Table (Art. 37 ISR)

| Bracket | From (\$) | To (\$) | Rate | Excess Over (\$) | Fixed Fee (\$) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **I** | \$0.01 | \$236.00 | **Exempt (0%)** | \$0.00 | \$0.00 |
| **II** | \$236.01 | \$447.62 | **10%** | \$236.00 | \$8.83 |
| **III** | \$447.63 | \$1,019.05 | **20%** | \$447.62 | \$30.00 |
| **IV** | \$1,019.06 | And above | **30%** | \$1,019.05 | \$144.28 |

---

## 4. Execution Formula
$$\text{Withholding} = \text{Round}\left([(\text{Net Taxable Base} - \text{Excess Over}) \times \text{Rate}] + \text{Fixed Fee}, 2\right)$$

If $\text{Net Taxable Base}$ falls within Bracket I, $\text{Withholding} = 0.00$.
All withholdings calculated under this skill must be summarized for line-item reporting on the company's monthly **Form F-14**.
