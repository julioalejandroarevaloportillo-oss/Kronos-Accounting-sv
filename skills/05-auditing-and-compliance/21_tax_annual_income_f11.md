---
name: tax-sv-annual-income-f11
description: Computes corporate and individual annual income tax returns (Declaración de Renta Anual - Formulario F-11), executing fiscal reconciliations, non-deductible expense adjustments, and tax rate determination.
version: 1.0.0
category: auditing-and-compliance
jurisdiction: El Salvador (SV)
regulatory_references: [Income Tax Law Art. 28, 29, 29-A, 41; Tax Code Art. 98]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 21: Annual Income Tax Return Preparer (Formulario F-11)

## 🎯 Purpose
Instruct AI agents to execute the annual fiscal closing, calculate corporate and individual **Annual Income Tax (*Impuesto sobre la Renta - F-11*)**, perform the book-to-tax reconciliation (*Conciliación Fiscal*), and offset monthly *Pago a Cuenta* prepayments.

---

## 1. Statutory Corporate Tax Rates (Art. 41 ISR)

For legal entities (*personas jurídicas*):

| Annual Taxable Gross Income | Corporate Income Tax Rate |
|---|:---:|
| **Equal to or less than \$150,000.00 USD** | **25.00%** |
| **Greater than \$150,000.00 USD** | **30.00%** |

---

## 2. Book-to-Tax Reconciliation (*Conciliación Fiscal*)

Accounting profit under IFRS rarely equals fiscal taxable income. The AI must adjust:

### Additions to Net Income (Non-Deductible Expenses - Art. 29-A ISR):
1. Expenses without formal tax documentation (missing DTEs or valid supplier NIT/NRC).
2. Penalties, fines, and late interest paid to tax authorities, municipalities, or social security.
3. Entertainment and travel expenses exceeding statutory caps without direct business justification.
4. Depreciation in excess of maximum statutory rates (Art. 30 ISR).
5. Donations exceeding the 20% net income limit.

### Deductions from Net Income (Non-Taxable Income):
1. Exempt income or foreign-source dividends already taxed under bilateral treaties.

$$\text{Fiscal Taxable Income} = \text{Accounting Net Profit} + \text{Non-Deductible Expenses} - \text{Exempt Income}$$
$$\text{Gross Income Tax Determined} = \text{Fiscal Taxable Income} \times \text{Tax Rate (25% or 30%)}$$

---

## 3. Offsetting Prepayments (Final F-11 Balance)

$$\text{Final Balance Payable (or Refund)} = \text{Gross Income Tax} - \sum \text{Pago a Cuenta Prepayments (F-14)} - \text{Fiscal Retentions Borne}$$

- **Filing Window:** January 1 to **April 30** of the year following the fiscal period.
