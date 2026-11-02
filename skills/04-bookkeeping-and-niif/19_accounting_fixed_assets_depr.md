---
name: accounting-sv-fixed-assets-depr
description: Computes fixed asset depreciation schedules under Salvadoran tax law (Art. 30 Ley de I.S.R.) and IFRS for SMEs, managing temporary book-to-tax timing differences.
version: 1.0.0
category: bookkeeping-and-niif
jurisdiction: El Salvador (SV)
regulatory_references: [Income Tax Law Art. 30; IFRS for SMEs Section 17 (Property, Plant and Equipment)]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📒 SKILL 19: Fixed Assets & Depreciation Engine

## 🎯 Purpose
Instruct AI agents to calculate, maintain, and post monthly depreciation schedules for Property, Plant, and Equipment, reconciling Salvadoran maximum statutory tax rates (*Ley de I.S.R.*) with IFRS useful life accounting.

---

## 1. Statutory Maximum Annual Depreciation Rates (Art. 30 ISR)

Under Art. 30 of the Salvadoran Income Tax Law, straight-line depreciation is deductible up to the following maximum percentages:

| Asset Class | Minimum Useful Life | Maximum Annual Tax Rate | Description / Examples |
|---|:---:|:---:|---|
| **Buildings & Structures** | 20 years | **5.00%** | Commercial warehouses, corporate buildings, structural improvements |
| **Machinery & Equipment** | 5 years | **20.00%** | Industrial plants, manufacturing machinery, generators |
| **Vehicles & Transport** | 4 years | **25.00%** | Delivery trucks, corporate vehicles, forklifts |
| **Computers & Software** | 2 years | **50.00%** | Servers, laptops, licensed business software |
| **Other Tangible Goods** | 5 years | **20.00%** | Office furniture, fixtures, security systems |

*Note on Land:* Land has an indefinite useful life and is **never** depreciated.

---

## 2. Monthly Depreciation Posting

For any depreciable asset with acquisition cost ($C$), salvage value ($S$), and annual tax rate ($R$):

$$\text{Monthly Tax Depreciation} = \frac{(C - S) \times R}{12}$$

### Standard Monthly Journal Entry:
```text
CÓDIGO    DESCRIPCIÓN DE LA CUENTA                    DEBE ($)       HABER ($)
---------------------------------------------------------------------------------
410208    Gastos de Administración: Depreciación        XXX.XX
120201    Depreciación Acumulada de Activos Fijos                       XXX.XX
---------------------------------------------------------------------------------
TOTALES:                                                XXX.XX          XXX.XX
```

---

## 3. Disposals and Capital Gains (Art. 42 ISR)
When an asset is retired, sold, or scrapped:
- Book value = $\text{Historical Cost} - \text{Accumulated Depreciation}$.
- If sold at a price higher than book value:
  - If held $\le 3$ years: The gain is ordinary taxable operating income.
  - If held $> 3$ years: The gain is classified as a **Capital Gain (*Ganancia de Capital*)**, taxed at a preferential rate of 10% under Art. 42 ISR.
