---
name: tax-sv-advance-income-tax-f14
description: Computes monthly Advance Income Tax (Pago a Cuenta 1.75%) and consolidates all Income Tax Withholdings (Art. 156, Art. 158, payroll) for monthly Salvadoran Form F-14.
version: 1.0.0
category: vat-and-monthly-taxes
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 151, 156, 158; Income Tax Law Art. 37]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 10: Advance Income Tax & Withholding Return (Formulario F-14)

## 🎯 Purpose
Guide AI agents to calculate the monthly **Advance Income Tax (*Pago a Cuenta*)** and consolidate all **Income Tax Withholdings** into a verified draft of **Form F-14** (*Declaración y Pago de Retenciones y Pago a Cuenta*).

---

## 1. Advance Income Tax (Pago a Cuenta - Art. 151 C.T.)

### General Rule:
Every legal entity and registered business individual must prepay income tax every month:
$$\text{Pago a Cuenta} = \text{Gross Monthly Operating Revenues} \times 0.0175 \quad (1.75\%)$$

- **Included Revenues:** Domestic taxable and exempt gross sales, export revenue, commissions, fees, and secondary operating income.
- **Excluded Revenues:** VAT Débito Fiscal, dividends already taxed, and capital gains from fixed assets held $>3$ years.
- **Special Reduced Rates:** Certain regulated activities (e.g. fuel retailing, pharmaceuticals with maximum regulated retail pricing) apply a reduced rate of **0.75%** upon DGII authorization.

---

## 2. Monthly Withholdings Consolidated in Form F-14

Form F-14 is the tax return where the company remits all income taxes withheld from third parties during the month:

1. **Payroll Withholdings (Art. 37 ISR):** Total income tax deducted from employees' salaries.
2. **Professional & Independent Services (Art. 156 C.T.):** 10% withheld on professional fees and DTE-14 purchases.
3. **Non-Resident Withholdings (Art. 158 C.T.):** 20% (or 25% for tax havens) on payments to foreign providers.
4. **Board of Directors / Statutory Auditor Fees:** 10% withheld on corporate board allowances (*dietas*).

---

## 3. Consolidation Draft for User

```text
======================================================================
DRAFT: FORM F-14 (ADVANCE INCOME TAX & WITHHOLDINGS) - YYYY-MM
======================================================================
[A] ADVANCE INCOME TAX (PAGO A CUENTA)
    - Total Gross Monthly Revenues:          $  XX,XXX.XX
    - Applicable Rate:                       1.75%
    - Pago a Cuenta Payable:                 $   X,XXX.XX

[B] INCOME TAX WITHHOLDINGS PAYABLE TO TREASURY
    - Employee Payroll Tax Withheld (Art. 37):$     XXX.XX
    - Professional Services Withheld (10%):  $     XXX.XX
    - Non-Resident Remittances Withheld (20%):$     XXX.XX
    - Other Retentions:                      $       0.00
    TOTAL WITHHOLDINGS LIQUIDITY:            $     XXX.XX
----------------------------------------------------------------------
TOTAL LIQUID CASH TO PAY IN BANK (F-14):     $   X,XXX.XX
======================================================================
```
