---
name: payroll-sv-isss-calculator
description: Calculates Salvadoran Social Security (ISSS) health contributions for employees and employers, enforcing the statutory $1,000.00 ceiling and payroll periodicity.
version: 1.0.0
category: payroll-and-labor
jurisdiction: El Salvador (SV)
regulatory_references: [Social Security Law Art. 29, 30; ISSS Contribution Regulation]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 👥 SKILL 11: Social Security (ISSS) Contribution Calculator

## 🎯 Purpose
Instruct AI agents to compute the mandatory health and maternity contributions to the Salvadoran Social Security Institute (**ISSS - Instituto Salvadoreño del Seguro Social**), applying official wage ceilings and deduction caps.

---

## 1. Statutory Parameters & Ceilings

### Wage Ceiling (*Techo Máximo Cotizable*):
- **Monthly Ceiling:** **\$1,000.00 USD**
- **Bi-weekly Ceiling:** **\$500.00 USD**
- **Weekly Ceiling:** **\$250.00 USD**

Any earnings above the ceiling are **exempt** from ISSS contributions.

### Contribution Rates:
| Contributor | Rate | Monthly Max Deduction | Bi-weekly Max Deduction |
|---|---|---|---|
| **Employee (Laboral)** | **3.00%** | **\$30.00 USD** | **\$15.00 USD** |
| **Employer (Patronal)** | **7.50%** | **\$75.00 USD** | **\$37.50 USD** |

---

## 2. Mathematical Algorithm

For any gross taxable earnings ($W$):

### Monthly Period:
$$\text{Base ISSS} = \min(W, 1000.00)$$
$$\text{ISSS Laboral} = \text{Round}(\text{Base ISSS} \times 0.03, 2)$$
$$\text{ISSS Patronal} = \text{Round}(\text{Base ISSS} \times 0.075, 2)$$

### Bi-weekly Period:
$$\text{Base ISSS} = \min(W, 500.00)$$
$$\text{ISSS Laboral} = \text{Round}(\text{Base ISSS} \times 0.03, 2)$$
$$\text{ISSS Patronal} = \text{Round}(\text{Base ISSS} \times 0.075, 2)$$

---

## 3. Inclusion & Exclusion Rules
- **Subject to ISSS:** Base salary, commissions, overtime, paid rest days, production bonuses.
- **Excluded from ISSS:** Annual mandatory vacation 30% surcharge, statutory Christmas bonus (*Aguinaldo*), severance pay, travel allowances (*viáticos* with receipts).
