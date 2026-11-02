---
name: dte-sv-invoice-parser-validator
description: Parses, validates, and audits Electronic Invoices (DTE-01) and Tax Credit Vouchers (DTE-03 CCF) according to El Salvador Ministry of Finance (Ministerio de Hacienda) schemas.
version: 1.0.0
category: dte-pipeline
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 119-G, 107; DTE Technical Specification v1.0-v3.0]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 01: Electronic Invoice & Tax Credit Validator (DTE-01 / DTE-03)

## 🎯 Purpose
Instruct any AI agent to ingest, validate, and audit Salvadoran Electronic Invoices (`tipoDte: "01"` - Factura Electrónica) and Tax Credit Vouchers (`tipoDte: "03"` - Comprobante de Crédito Fiscal - CCF), verifying JSON structure integrity, arithmetic correctness, and tax compliance.

---

## 1. Document Type Rules

### DTE-01: Factura Electrónica (Final Consumer)
- **Target Audience:** Non-taxpayer individuals or end consumers.
- **Price Structure:** Item unit prices (`precioUni`) **already include the 13% VAT**.
- **Net Base Extraction:**
  $$\text{Net Taxable Base} = \frac{\text{Venta Gravada}}{1.13}$$
  $$\text{Embedded VAT (13%)} = \text{Venta Gravada} - \text{Net Taxable Base}$$

### DTE-03: Comprobante de Crédito Fiscal (CCF)
- **Target Audience:** Registered VAT taxpayers (holding a valid NRC).
- **Price Structure:** Item unit prices (`precioUni`) are **net without VAT**.
- **VAT Calculation:**
  $$\text{Item VAT} = \text{Round}(\text{ventaGravada} \times 0.13, 2)$$
  $$\text{Total Subtotal} = \text{totalGravada} + \text{Total VAT}$$

---

## 2. Core JSON Schema Fields (Ministry of Finance)

Any AI parsing a Salvadoran DTE must verify:

```json
{
  "identificacion": {
    "version": 1,
    "ambiente": "01",
    "tipoDte": "03",
    "numeroControl": "DTE-03-M001P001-000000000000001",
    "codigoGeneracion": "3F2504E0-4F89-11D3-9A0C-0305E82C3301",
    "fecEmi": "2026-11-01",
    "horEmi": "10:15:30",
    "tipoMoneda": "USD"
  },
  "emisor": {
    "nit": "06140101901011",
    "nrc": "1234567",
    "nombre": "DISTRIBUIDORA CENTRAL S.A. DE C.V.",
    "codActividad": "46900"
  },
  "receptor": {
    "tipoDocumento": "36",
    "numDocumento": "06140202951022",
    "nrc": "7654321",
    "nombre": "CLIENTE INDUSTRIAL S.A. DE C.V."
  },
  "resumen": {
    "totalGravada": 1000.00,
    "tributos": [
      { "codigo": "20", "descripcion": "Impuesto al Valor Agregado 13%", "valor": 130.00 }
    ],
    "subTotal": 1130.00,
    "ivaRete1": 10.00,
    "totalPagar": 1120.00,
    "condicionOperacion": 1
  }
}
```

---

## 3. Strict Validation Checklist

1. **UUID Format:** `codigoGeneracion` must be an uppercase RFC-4122 UUID v4 (`^[0-9A-F]{8}-[0-9A-F]{4}-4[0-9A-F]{3}-[89AB][0-9A-F]{3}-[0-9A-F]{12}$`).
2. **Control Number Format:** `numeroControl` must follow `^DTE-(01|03)-[A-Z0-9]{8}-[0-9]{15}$`.
3. **VAT Rounding Rule:** Monetary calculations must use 2-decimal standard financial half-up rounding (`ROUND_HALF_UP`).
4. **Large Taxpayer Withholding Check:** If `receptor` is a designated Large Taxpayer (*Gran Contribuyente*) and `totalGravada` $\ge \$100.00$, verify that `ivaRete1` equals $\text{Round}(\text{totalGravada} \times 0.01, 2)$.

---

## 4. Agent Output Protocol
Return a structured audit report with:
- **Status:** `VALID`, `WARNING (Minor Rounding)`, or `INVALID`.
- **Extracted Header:** Date, Generation Code, Control Number, Issuer NIT/NRC, Receiver NIT/NRC.
- **Financial Breakdown:** Net Taxable, Exempt, Non-Subject, VAT (13%), 1% Withholding, Net Total Payable.
