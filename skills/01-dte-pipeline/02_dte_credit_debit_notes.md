---
name: dte-sv-credit-debit-notes
description: Processes, reconciles, and audits Electronic Credit Notes (DTE-05) and Debit Notes (DTE-06), linking adjustments to original DTEs and adjusting VAT debit/credit balances.
version: 1.0.0
category: dte-pipeline
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 110, 111; DTE Specification DTE-05 & DTE-06]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 02: Credit & Debit Note Management (DTE-05 / DTE-06)

## 🎯 Purpose
Guide AI agents in parsing, linking, and accounting for Salvadoran Electronic Credit Notes (`tipoDte: "05"`) and Debit Notes (`tipoDte: "06"`). These documents legally increase or decrease previously billed amounts, VAT debits/credits, and accounts receivable/payable.

---

## 1. Document Mechanics

| Type | Name | Effect on Balances | Effect on VAT |
|---|---|---|---|
| **DTE-05** | Nota de Crédito | Decreases A/R or A/P (Returns, discounts, price adjustments) | Reduces Issuer's VAT Debit / Reduces Buyer's VAT Credit |
| **DTE-06** | Nota de Débito | Increases A/R or A/P (Late fees, additional charges, under-billing) | Increases Issuer's VAT Debit / Increases Buyer's VAT Credit |

---

## 2. Linkage to Original Reference Document

A valid Credit or Debit Note must include the `documentoRelacionado` object pointing to the original DTE:

```json
{
  "documentoRelacionado": [
    {
      "tipoDocumento": "03",                                  // Referenced DTE type (e.g. CCF)
      "tipoGeneracion": 2,                                    // 1: Physical Paper, 2: Electronic DTE
      "numeroDocumento": "3F2504E0-4F89-11D3-9A0C-0305E82C3301", // Generation Code of original DTE
      "fechaEmision": "2026-10-25"
    }
  ]
}
```

---

## 3. Arithmetic & Tax Rules

### Credit Note (DTE-05):
1. **Upper Bound Check:** The taxable base and VAT on a Credit Note cannot exceed the remaining unsettled balance of the referenced original document.
2. **Partial vs. Total Return:**
   $$\text{Adjusted VAT} = \text{Round}(\text{montoDevolucionORebaja} \times 0.13, 2)$$
3. **Withholding Reversal:** If the original transaction had 1% VAT withholding (Art. 162), the Credit Note must proportionally reverse `ivaRete1`.

### Debit Note (DTE-06):
1. **Additional VAT Calculation:**
   $$\text{Additional VAT} = \text{Round}(\text{recargoOInteres} \times 0.13, 2)$$
2. **Withholding Application:** If the new accumulated balance exceeds \$100.00 and parties are Large Taxpayers, apply 1% withholding on the debit note increment.

---

## 4. Agent Execution Steps
1. Parse `documentoRelacionado` and match it against the transaction ledger.
2. Verify that the adjustment reason is explicitly stated (`motivo`).
3. Compute the net impact on both the VAT Subledger and Customer/Vendor Statement.
4. Output the adjusted journal entry and VAT ledger line item.
