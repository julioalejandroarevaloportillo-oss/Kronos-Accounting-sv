---
name: tax-sv-form-f07-preparer
description: Prepares, reconciles, and calculates the monthly Salvadoran VAT Return (Declaración de IVA - Formulario F-07), computing debit/credit netting, tax surplus carryover, and final payment obligations.
version: 1.0.0
category: vat-and-monthly-taxes
jurisdiction: El Salvador (SV)
regulatory_references: [Tax Code Art. 93, 94; Executive Decree 497 (VAT Regulations)]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 09: Monthly VAT Return Preparer (Formulario F-07)

## 🎯 Purpose
Instruct AI agents to execute the monthly tax settlement between accumulated **VAT Débito Fiscal** and **VAT Crédito Fiscal**, preparing an error-free draft of **Form F-07** for filing on the DGII tax portal (*Dirección General de Impuestos Internos*).

---

## 1. Filing Deadlines & Legal Rules

- **Statutory Due Date:** Within the first **10 business days** of the month following the tax period (Art. 94 C.T.).
- **Required Inputs:**
  1. Monthly total from *Libro de Compras* (Skill 06).
  2. Monthly total from *Libro de Ventas a Contribuyentes* (Skill 07).
  3. Monthly total from *Libro de Ventas a Consumidor Final* (Skill 08).
  4. Prior month's VAT Tax Surplus carryover (*Remanente de Crédito Fiscal del mes anterior*), if any.
  5. Total 1% VAT Withholdings deducted by clients (*IVA Retenido por Clientes*).
  6. Total 1% VAT Withholdings practiced to vendors (*IVA Retenido a Terceros*).

---

## 2. Core Settlement Algorithm

```python
# 1. Total Output Tax (Débito Fiscal)
total_debito = debito_ventas_contribuyentes + debito_ventas_consumidores

# 2. Total Input Tax (Crédito Fiscal) available for offset
total_credito = credito_compras_locales + credito_importaciones + remanente_mes_anterior

# 3. Monthly Net Balance Determination
balance = total_debito - total_credito

if balance > 0:
    # Tax liability incurred
    impuesto_iva_determinado = balance
    remanente_credito_proximo_mes = 0.00
else:
    # Surplus tax credit carried over
    impuesto_iva_determinado = 0.00
    remanente_credito_proximo_mes = abs(balance)

# 4. Offset Client Withholdings (1% borne)
saldo_despues_retenciones = max(0.00, impuesto_iva_determinado - iva_retenido_por_clientes)
remanente_retenciones_proximo_mes = max(0.00, iva_retenido_por_clientes - impuesto_iva_determinado)

# 5. Add Withholdings Practiced to Vendors (Must be paid regardless of credits)
# Withholdings practiced to third parties CANNOT be offset against credit fiscal!
total_a_pagar_f07 = saldo_despues_retenciones + iva_retenido_a_terceros
```

---

## 3. Standard Output Draft for User

```text
======================================================================
DRAFT: FORM F-07 (MONTHLY VAT DECLARATION) - Period: YYYY-MM
======================================================================
[A] DETERMINATION OF OUTPUT TAX (DÉBITO FISCAL)
    - Sales to Taxpayers Base:               $  XX,XXX.XX
    - Sales to Taxpayers Output Tax:         $   X,XXX.XX
    - Sales to Consumers Base:               $  XX,XXX.XX
    - Sales to Consumers Output Tax:         $   X,XXX.XX
    TOTAL OUTPUT TAX (DÉBITO FISCAL):        $  XX,XXX.XX

[B] DETERMINATION OF INPUT TAX (CRÉDITO FISCAL)
    - Domestic Purchases Tax Credit:         $   X,XXX.XX
    - Import Purchases Tax Credit:           $     XXX.XX
    - Prior Month Tax Credit Surplus:        $     XXX.XX
    TOTAL INPUT TAX (CRÉDITO FISCAL):        $  XX,XXX.XX

[C] FISCAL POSITION
    - Net VAT Determined (Payable):          $   X,XXX.XX  (or $0.00)
    - Surplus Credit for Next Month:         $       0.00  (or $X,XXX.XX)
    - Less: 1% VAT Withheld by Clients:     -$     XXX.XX
    - Subtotal VAT Payable:                  $   X,XXX.XX
    - Plus: 1% VAT Withheld to Vendors:     +$     XXX.XX
----------------------------------------------------------------------
TOTAL LIQUID CASH TO PAY IN BANK (F-07):     $   X,XXX.XX
======================================================================
```
