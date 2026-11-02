---
name: dte-sv-excluded-subjects
description: Handles Electronic Invoices for Excluded Subjects (DTE-14 Factura de Sujeto Excluido), managing purchases from non-VAT registered individuals and 10% Income Tax Withholding under Tax Code Art. 156.
version: 1.0.0
category: dte-pipeline
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 119-E, Art. 156; Income Tax Law Art. 29]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 04: Excluded Subject Invoicing & 10% Withholding (DTE-14)

## 🎯 Purpose
Instruct AI agents to process, validate, and record purchases from non-VAT registered natural persons using **DTE-14 (Factura de Sujeto Excluido)**, ensuring correct application of the **10% Income Tax Withholding (Art. 156 C.T.)** and cost deductibility.

---

## 1. When to Issue a DTE-14

- **Issuer:** The buyer (registered company or formal business taxpayer).
- **Vendor (Sujeto Excluido):** An individual (*persona natural*) providing goods or independent services who is **not registered as a VAT taxpayer** (no NRC).
- **Examples:** Plumber, electrician, independent artisan, agricultural supplier without NRC, occasional freelance consultant.

---

## 2. Tax Mechanics & Withholding

1. **No VAT (13%):** DTE-14 does **NOT** incur VAT (0% VAT).
2. **Income Tax Withholding (10% ISR - Art. 156 C.T.):**
   - Applies to **services, labor, or professional consulting** performed by individuals.
   - Does **not** apply to the purchase of raw agricultural goods or used personal goods unless specifically required by sectoral regulations.
   $$\text{Income Tax Withheld} = \text{Round}(\text{totalCompra} \times 0.10, 2)$$
   $$\text{Net Amount Paid to Vendor} = \text{totalCompra} - \text{Income Tax Withheld}$$

---

## 3. DTE-14 JSON Payload Example

```json
{
  "identificacion": {
    "version": 1,
    "tipoDte": "14",
    "numeroControl": "DTE-14-M001P001-000000000000001",
    "codigoGeneracion": "9B1B1A56-34A2-4D3B-BA67-123456789ABC",
    "fecEmi": "2026-11-01"
  },
  "sujetoExcluido": {
    "tipoDocumento": "13",                                    // 13: DUI
    "numDocumento": "012345678",
    "nombre": "JUAN PEREZ (ALBAÑIL INDEPENDIENTE)",
    "direccion": {
      "departamento": "06",                                  // San Salvador
      "municipio": "14",
      "complemento": "Colonia Escalon, Pasaje 2, Casa 15"
    }
  },
  "cuerpoDocumento": [
    {
      "numItem": 1,
      "tipoItem": 2,                                         // 2: Service
      "cantidad": 1.0,
      "descripcion": "Reparacion de instalaciones electricas de oficina",
      "precioUni": 300.00,
      "compra": 300.00
    }
  ],
  "resumen": {
    "totalCompra": 300.00,
    "reteRenta": 30.00,                                      // 10% Withholding
    "totalPagar": 270.00,
    "totalLetras": "DOSCIENTOS SETENTA 00/100 USD"
  }
}
```

---

## 4. Bookkeeping & Tax Declaration Routing

- **VAT Ledger:** Recorded in the **Purchases Ledger (*Libro de Compras*)** in the designated column *"Compras a Sujetos Excluidos"*.
- **Tax Return F-14:** The \$30.00 withheld must be reported and paid in monthly **Form F-14** under *Retenciones Art. 156 C.T.*.
- **Annual Return F-910 / F-11:** Recorded for vendor year-end certificates and tax deductibility of corporate expenses.
