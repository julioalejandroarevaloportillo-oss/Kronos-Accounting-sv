---
name: accounting-sv-closing-statements
description: Automates monthly and year-end financial statement preparation (Balance Sheet, Income Statement) and statutory closing entries (Legal Reserve 7% under Commercial Code Art. 123).
version: 1.0.0
category: bookkeeping-and-niif
jurisdiction: El Salvador (SV)
regulatory_references: [Commercial Code Art. 123, 442; IFRS for SMEs Section 3 to 6]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📒 SKILL 20: Financial Statement Generator & Statutory Year-End Closing

## 🎯 Purpose
Guide AI agents to aggregate trial balances, generate official financial statements (**Balance General** and **Estado de Resultados**), compute the statutory **7% Legal Reserve**, and execute year-end closing entries.

---

## 1. Statutory Legal Reserve (*Reserva Legal* - Art. 123 C.Com)

Under the Salvadoran Commercial Code, capital corporations (*Sociedades Anónimas* and *Sociedades de Responsabilidad Limitada*) must set aside profits before distributing dividends:

- **Annual Allocation Rate:** **7.00%** of net annual profits after income tax.
- **Statutory Ceiling:** Must continue annually until the reserve reaches **at least 20% (one-fifth) of the company's total capital stock (*Capital Social*)**.

$$\text{Legal Reserve Deduction} = \text{Net Profit After Tax} \times 0.07$$

---

## 2. Year-End Closing Journal Entry Sequence

### Step 1: Close Revenue Accounts
Debit all Revenue accounts (Class 6) to zero, credit Account `5101 Pérdidas y Ganancias`.

### Step 2: Close Expense Accounts
Credit all Expense accounts (Class 4) to zero, debit Account `5101 Pérdidas y Ganancias`.

### Step 3: Record Corporate Income Tax Liability
Determine tax expense (30% general rate, or 25% if annual revenues $\le \$150,000.00$), debit Income Tax expense and credit `2107 Pasivo por Impuesto sobre la Renta`.

### Step 4: Transfer Net Profit & Record Legal Reserve
```text
CÓDIGO    DESCRIPCIÓN DE LA CUENTA                    DEBE ($)       HABER ($)
---------------------------------------------------------------------------------
510101    Pérdidas y Ganancias (Cierre)               XX,XXX.XX
310201    Reserva Legal (7% Art. 123 C.Com)                            X,XXX.XX
310401    Resultado del Ejercicio (Utilidad Neta)                     XX,XXX.XX
---------------------------------------------------------------------------------
```

---

## 3. Financial Statement Formats

The agent outputs:
1. **Balance Sheet (*Estado de Situación Financiera*):** Current Assets, Non-Current Assets, Current Liabilities, Non-Current Liabilities, Equity ($Assets \equiv Liabilities + Equity$).
2. **Income Statement (*Estado de Resultados Integral*):** Revenues - Cost of Goods Sold = Gross Profit - Operating Expenses = Operating Income - Financial Expenses = Pre-tax Income - Income Tax = Net Income.
