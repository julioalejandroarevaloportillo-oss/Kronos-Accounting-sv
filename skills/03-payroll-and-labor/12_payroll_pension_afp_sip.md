---
name: payroll-sv-pension-afp-sip
description: Calculates contributions to the Salvadoran Integrated Pension System (AFP Crecer, AFP Confía, SIP) for employees and employers, verifying statutory percentages.
version: 1.0.0
category: payroll-and-labor
jurisdiction: El Salvador (SV)
regulatory_references: [Integrated Pension System Law Art. 16, 17; Special Pension Decrees]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 👥 SKILL 12: Integrated Pension System (AFP / SIP) Calculator

## 🎯 Purpose
Instruct AI agents to calculate mandatory pension contributions to Pension Fund Administrators (**AFP Crecer**, **AFP Confía**, and the **Sistema Integrado de Pensiones - SIP**), verifying employee deductions and employer obligations.

---

## 1. Statutory Contribution Rates

Unlike ISSS (which has a \$1,000 ceiling), pension contributions are calculated across the **full gross devengado** of the employee:

| Contributor | Statutory Rate | Destination / Allocation |
|---|---|---|
| **Employee (Laboral)** | **7.25%** | Individual Savings Account (*Cuenta Individual de Ahorro para Pensiones*) |
| **Employer (Patronal)** | **8.75%** | Solidarity Fund + Disability/Survivors Insurance + Administrator Commission |
| **Total Combined Contribution** | **16.00%** | Full Pension System Contribution |

---

## 2. Mathematical Algorithm

For any gross taxable earnings ($W$):

$$\text{AFP Laboral} = \text{Round}(W \times 0.0725, 2)$$
$$\text{AFP Patronal} = \text{Round}(W \times 0.0875, 2)$$
$$\text{Total Aporte AFP} = \text{AFP Laboral} + \text{AFP Patronal} = \text{Round}(W \times 0.16, 2)$$

---

## 3. Inclusion & Exclusion Rules
- **Subject to AFP:** Base wages, commissions, performance bonuses, overtime, paid vacation time.
- **Excluded from AFP:** Statutory Christmas bonus (*Aguinaldo*), statutory severance pay (*Indemnización por despido*), documented expense reimbursements.
- **Verification Rule:** The sum of `AFP Laboral` + `AFP Patronal` must equal 16% of total taxable earnings within a ±\$0.01 rounding tolerance.
