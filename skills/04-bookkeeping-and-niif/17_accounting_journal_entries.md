---
name: accounting-sv-automated-journal-entries
description: Generates balanced double-entry accounting journal entries (partidas de diario) from commercial operations, DTE invoices, vendor vouchers, and tax liquidations.
version: 1.0.0
category: bookkeeping-and-niif
jurisdiction: El Salvador (SV)
regulatory_references: [Commercial Code Art. 436, 439; IFRS for SMEs Section 2]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📒 SKILL 17: Automated Double-Entry Journal Entry Generator

## 🎯 Purpose
Instruct AI agents to convert commercial events, DTE invoices, payroll rosters, and monthly tax returns into **strictly balanced double-entry journal entries (*Partidas de Diario*)** adhering to Salvadoran accounting norms.

---

## 1. Cardinal Double-Entry Law

$$\sum \text{DEBE (Debits)} \equiv \sum \text{HABER (Credits)}$$
Any difference $> \$0.00$ violates accounting law and invalidates the entry.

---

## 2. Standard Transaction Patterns

### Pattern A: B2B Credit Sale with 1% VAT Withholding (DTE-03)
*Scenario:* Company sells \$1,000.00 of goods to a Large Taxpayer on credit.
- Net Sale: \$1,000.00
- 13% VAT Débito: \$130.00
- 1% VAT Withholding Borne: \$10.00
- Net Account Receivable: \$1,120.00

```text
CÓDIGO    DESCRIPCIÓN DE LA CUENTA                    DEBE ($)       HABER ($)
---------------------------------------------------------------------------------
110301    Cuentas por Cobrar Clientes                 1,120.00
110803    IVA Retenido por Clientes (1% Art. 162)        10.00
610101    Ingresos por Ventas Gravadas                               1,000.00
210701    IVA Débito Fiscal (13%)                                      130.00
---------------------------------------------------------------------------------
TOTALES:                                              1,130.00       1,130.00
```

---

### Pattern B: Purchase with 1% VAT Withholding Practiced (DTE-03 + DTE-07)
*Scenario:* Large Taxpayer purchases \$2,000.00 of inventory from a medium taxpayer on credit.
- Net Inventory: \$2,000.00
- 13% VAT Crédito: \$260.00
- 1% VAT Withholding to Remit: \$20.00
- Vendor Payable: \$2,240.00

```text
CÓDIGO    DESCRIPCIÓN DE LA CUENTA                    DEBE ($)       HABER ($)
---------------------------------------------------------------------------------
110901    Inventario de Mercaderías                   2,000.00
110801    IVA Crédito Fiscal                            260.00
210101    Cuentas por Pagar Proveedores                              2,240.00
210702    IVA Retenido a Terceros (1% Art. 162)                         20.00
---------------------------------------------------------------------------------
TOTALES:                                              2,260.00       2,260.00
```

---

### Pattern C: Monthly VAT Settlement (Form F-07)
*Scenario:* Month closes with \$1,500.00 Débito Fiscal and \$1,100.00 Crédito Fiscal, plus \$20.00 client withholding credit. Net payment: \$380.00 via bank transfer.

```text
CÓDIGO    DESCRIPCIÓN DE LA CUENTA                    DEBE ($)       HABER ($)
---------------------------------------------------------------------------------
210701    IVA Débito Fiscal                           1,500.00
110801    IVA Crédito Fiscal                                         1,100.00
110803    IVA Retenido por Clientes                                     20.00
110102    Bancos Locales (Pago F-07)                                   380.00
---------------------------------------------------------------------------------
TOTALES:                                              1,500.00       1,500.00
```
