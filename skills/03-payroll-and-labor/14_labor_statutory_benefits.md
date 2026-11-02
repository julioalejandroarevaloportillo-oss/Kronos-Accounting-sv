---
name: labor-sv-statutory-benefits
description: Calculates mandatory Salvadoran employee benefits and indemnities, including annual leave (vacaciones), Christmas bonus (aguinaldo), and severance pay (Art. 58).
version: 1.0.0
category: payroll-and-labor
jurisdiction: El Salvador (SV)
regulatory_references: [Labor Code Arts. 58, 177, 187, 196-202]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 👥 SKILL 14: Statutory Employee Benefits & Severance Pay

## 🎯 Purpose
Instruct AI agents to calculate mandatory statutory labor benefits under the Salvadoran Labor Code (*Código de Trabajo*), covering annual paid vacation, statutory Christmas bonuses (*Aguinaldo*), and dismissal indemnities.

---

## 1. Annual Paid Vacation (*Vacación Anual* - Art. 177 C.T.)

- **Eligibility:** After **1 continuous year of service** with the same employer (minimum 200 days worked).
- **Duration:** **15 continuous calendar days** of paid rest.
- **Remuneration Formula:** 15 days of base salary **plus a 30% statutory surcharge**:
  $$\text{Daily Salary} = \frac{\text{Monthly Base Salary}}{30}$$
  $$\text{Vacation Pay} = (\text{Daily Salary} \times 15) \times 1.30$$

---

## 2. Christmas Bonus (*Aguinaldo* - Arts. 196-202 C.T.)

- **Payment Window:** Must be disbursed between **December 12 and December 20** of each year.
- **Tenure Brackets:**
  | Seniority on Dec 12 | Statutory Bonus Amount |
  |---|---|
  | **1 year to < 3 years** | **15 days of salary** |
  | **3 years to < 10 years** | **19 days of salary** |
  | **10 years or more** | **21 days of salary** |
  | **Less than 1 year** | Pro-rated: $\frac{\text{Days Worked}}{365} \times 15 \times \text{Daily Salary}$ |
- **Tax Exemption:** The Legislative Assembly typically passes an annual decree exempting Christmas bonuses up to a certain threshold (e.g. up to \$1,500.00 or up to 2-3 minimum wages) from income tax and social security.

---

## 3. Severance Pay for Unjustified Dismissal (*Indemnización* - Art. 58 C.T.)

- **General Rule:** **1 month's basic salary (30 days)** for each year of service, and proportionally for fractional years.
- **Statutory Ceiling:** The daily salary for indemnity purposes **cannot exceed 4 times the daily minimum wage** of the corresponding business sector.
- **Proportional Entitlements on Termination:** On any termination, the employer must also pay proportional accrued vacation (*vacación proporcional*) and proportional accrued Christmas bonus (*aguinaldo proporcional*).
