---
name: dte-sv-retention-vouchers
description: Ingests, audits, and generates Electronic Retention Vouchers (DTE-07 Comprobante de Retención) for 1% VAT Withholding under Tax Code Art. 162.
version: 1.0.0
category: dte-pipeline
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 162, 162-A, 163; MH Executive Decrees on Withholding Agents]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 03: VAT Withholding Voucher Management (DTE-07)

## 🎯 Purpose
Provide AI agents with the logic to process, audit, and generate Electronic Withholding Vouchers (`tipoDte: "07"` - Comprobante de Retención), validating the 1% VAT withholding regime enacted by El Salvador's Ministry of Finance.

---

## 1. Regulatory Framework: 1% VAT Withholding (Art. 162 C.T.)

### Qualification:
- **Issuer of DTE-07:** Designated **Large Taxpayers (*Grandes Contribuyentes*)** acting as Withholding Agents (*Agentes de Retención*).
- **Target Vendor:** Medium or Other Taxpayers (*Medianos y Otros Contribuyentes*).
- **Threshold:** Net purchase amount (excluding VAT) must be **equal to or greater than \$100.00 USD**.

### Exclusions from Withholding:
- Transactions between two Large Taxpayers (no withholding applies).
- Purchases under \$100.00 USD before VAT.
- Purchases from state entities or public utilities regulated under special decrees.

---

## 2. Structure of DTE-07 Body (`cuerpoDocumento`)

Unlike standard invoices, each item in a DTE-07 references an invoice being settled:

```json
{
  "cuerpoDocumento": [
    {
      "numItem": 1,
      "tipoDte": "03",                                        // Referenced document type (CCF)
      "tipoDoc": 2,                                            // 1: Paper, 2: Electronic
      "numDocumento": "3F2504E0-4F89-11D3-9A0C-0305E82C3301", // Generation Code of CCF
      "fechaEmision": "2026-11-01",
      "montoSujeto": 1000.00,                                 // Base amount without VAT
      "ivaRetenido": 10.00                                    // 1% of montoSujeto
    }
  ],
  "resumen": {
    "totalSujetoRetencion": 1000.00,
    "totalIvaRetenido": 10.00,
    "totalLetras": "DIEZ 00/100 USD"
  }
}
```

---

## 3. Audit & Cross-Checking Algorithm

1. **Base Verification:**
   $$\text{Expected Withholding} = \text{Round}(\text{montoSujeto} \times 0.01, 2)$$
   Verify that $|\text{ivaRetenido} - \text{Expected Withholding}| = 0.00$.
2. **Double Dip Prevention:** Verify that withholding has not been previously recorded for the same `numDocumento`.
3. **Tax Return Routing:**
   - **For the Withholding Agent (Buyer):** Record as a liability payable to the treasury in monthly tax return **Form F-07** (Row: *IVA Retenido a Terceros*).
   - **For the Withheld Vendor (Seller):** Record as an asset (*IVA Retenido por Clientes*) deductible against their own VAT payable in **Form F-07**.
