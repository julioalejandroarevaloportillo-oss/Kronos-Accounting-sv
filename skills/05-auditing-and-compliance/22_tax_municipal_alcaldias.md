---
name: tax-sv-municipal-alcaldias
description: Computes municipal business taxes and prepares annual asset declarations (Declaración Jurada de Activo Municipal) across Salvadoran municipalities (San Salvador, Santa Tecla, Antiguo Cuscatlán).
version: 1.0.0
category: auditing-and-compliance
jurisdiction: El Salvador (SV)
regulatory_references: [General Municipal Tax Code; Municipal Tax Tariffs of San Salvador and La Libertad]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📑 SKILL 22: Municipal Taxes & Asset Declarations (Alcaldías SV)

## 🎯 Purpose
Guide AI agents to compute local municipal commercial taxes (*Impuestos Municipales*) and prepare the mandatory **Annual Sworn Declaration of Net Assets (*Declaración Jurada de Activo Municipal*)** across major Salvadoran municipal jurisdictions.

---

## 1. Mechanics of Salvadoran Municipal Taxation

Unlike national taxes (which tax revenue or value added), Salvadoran municipal commercial taxes are primarily assessed on the **Taxable Net Assets (*Activo Imponible*)** located within each municipality where the business operates branches, offices, or factories:

$$\text{Taxable Municipal Asset} = \text{Total Assets} - \text{Deductions Permitted by Municipal Tariff}$$

### Allowable Municipal Asset Deductions:
- Assets physically located in other municipalities (proven by branch balance sheets).
- Registered investments in equity of other Salvadoran companies (to prevent double taxation).
- Cash balances held in foreign bank accounts (depending on specific municipal ordinances).
- Certain government bonds and tax-exempt securities.

---

## 2. Municipal Tax Calculation

Each municipality operates under its own statutory tax tariff (*Ley de Tarifa de Arbitrios Municipales*):
- **San Salvador Centro (Capital):** Progressive multi-tiered brackets assessing a base monthly fee plus a variable rate per thousand dollars (\$1,000) of net asset.
- **La Libertad Este (Santa Tecla, Antiguo Cuscatlán):** Tiered asset rates with special licenses for commercial and industrial establishments.

---

## 3. Mandatory Annual Deadlines
- **Annual Sworn Declaration (*Declaración de Activo*):** Must be submitted between **January 1 and March 31** (or April 30 depending on municipality) accompanied by the audited Balance Sheet certified by a licensed Salvadoran CPA (*Contador Público Autorizado*).
- **Monthly Tax Ticket (*Recibo Municipal Mensual*):** Issued monthly by the municipality based on the declared asset schedule.
