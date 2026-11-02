---
name: accounting-sv-bank-reconciliation
description: Executes automated bank reconciliations between internal cash ledgers and bank statements from major Salvadoran financial institutions (Banco Agrícola, BAC Credomatic, Banco Cuscatlán, Banco Davivienda).
version: 1.0.0
category: bookkeeping-and-niif
jurisdiction: El Salvador (SV)
regulatory_references: [Commercial Code Art. 440; Internal Control Best Practices]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📒 SKILL 18: Bank Reconciliation Engine (Salvadoran Banking)

## 🎯 Purpose
Guide AI agents to match, reconcile, and balance internal accounting cash ledgers against bank statements exported from major Salvadoran commercial banks (**Banco Agrícola**, **BAC Credomatic**, **Banco Cuscatlán**, **Banco Davivienda**, **Promerica**).

---

## 1. Reconciliation Equation

$$\text{Bank Statement Balance} + \text{Deposits in Transit} - \text{Outstanding Checks} \pm \text{Bank Errors} = \text{Adjusted Bank Balance}$$
$$\text{Internal Ledger Balance} + \text{Direct Bank Credits} - \text{Direct Bank Debits/Fees} \pm \text{Book Errors} = \text{Adjusted Book Balance}$$

**Condition of Success:** $\text{Adjusted Bank Balance} \equiv \text{Adjusted Book Balance}$.

---

## 2. Common Salvadoran Banking Patterns

When parsing CSV/Excel statements from local banks, the AI must classify:
1. **Direct Credits (Abonos):**
   - Customer wire transfers via **Transfer365** (ACH local interbank network).
   - POS card sales batch settlements (Net of card commission and 2% VAT perception if applicable).
2. **Direct Debits (Cargos):**
   - Monthly bank account maintenance fees (*Comisión por manejo de cuenta*).
   - Wire transfer fees (*Comisión Transfer365 Business*).
   - Tax debits: Electronic payment of taxes (F-07, F-14 via NPE banking portal).
   - Loan installment debits (Principal amortization vs. interest expense).
3. **Uncleared Items:**
   - Outstanding physical checks (*Cheques en tránsito*) issued to vendors not yet cashed.

---

## 3. Output Reconciliation Statement Format

The agent must output a clean reconciliation report identifying:
- Book Balance vs. Bank Balance.
- List of Matched Transactions (with matching confidence score).
- Unmatched Bank Items (requiring adjusting journal entries).
- Unmatched Book Items (pending bank processing).
- Proposed Adjusting Journal Entries (for bank fees, interest, and unrecorded customer ACH transfers).
