---
name: accounting-sv-standard-chart-of-accounts
description: Provides the standardized Salvadoran Chart of Accounts under IFRS for SMEs (NIIF para PYMES) approved by the Public Accounting Surveillance Board (CVPCPA).
version: 1.0.0
category: bookkeeping-and-niif
jurisdiction: El Salvador (SV)
regulatory_references: [Commercial Code Art. 435; CVPCPA Accounting Standards; IFRS for SMEs]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 📒 SKILL 16: Standardized Salvadoran Chart of Accounts (CVPCPA)

## 🎯 Purpose
Provide AI agents with the statutory accounting codification structure enforced in El Salvador by the **Consejo de Vigilancia de la Profesión de Contaduría Pública y Auditoría (CVPCPA)** and the **Código de Comercio**.

---

## 1. Top-Level Account Classification

In El Salvador, account numbers follow a standardized hierarchical decimal system:

```text
1. ACTIVO (ASSETS)
   11. ACTIVO CORRIENTE (CURRENT ASSETS)
       1101. Efectivo y Equivalentes de Efectivo
       1102. Inversiones a Corto Plazo
       1103. Cuentas y Documentos por Cobrar Comerciales
       1108. Cuentas por Cobrar Fiscales (Impuestos Soportados)
             110801. IVA Crédito Fiscal
             110802. Pago a Cuenta del ISR
             110803. IVA Retenido por Clientes (1% Art. 162)
             110804. IVA Percibido Soportado
       1109. Inventarios
   12. ACTIVO NO CORRIENTE (NON-CURRENT ASSETS)
       1201. Propiedad, Planta y Equipo
       1202. Depreciación Acumulada (Cuenta complementaria acreedora)
       1203. Activos Intangibles

2. PASIVO (LIABILITIES)
   21. PASIVO CORRIENTE (CURRENT LIABILITIES)
       2101. Cuentas y Documentos por Pagar Comerciales (Proveedores)
       2102. Préstamos Bancarios a Corto Plazo
       2103. Beneficios a Empleados por Pagar
       2107. Obligaciones y Retenciones Fiscales por Pagar
             210701. IVA Débito Fiscal
             210702. IVA Retenido a Terceros (1% Art. 162)
             210703. Retenciones de Renta Empleados (Art. 37)
             210704. Retenciones de Renta Servicios Profesionales (10% Art. 156)
             210705. Seguridad Social por Pagar (ISSS)
             210706. Pensiones por Pagar (AFP)
             210707. INCAF por Pagar
             210708. Pago a Cuenta por Pagar
   22. PASIVO NO CORRIENTE (NON-CURRENT LIABILITIES)
       2201. Obligaciones Financieras a Largo Plazo

3. PATRIMONIO (EQUITY)
   31. CAPITAL Y RESERVAS
       3101. Capital Social (Pagado / Suscrito)
       3102. Reserva Legal (7% de utilidades netas, Art. 123 C.Com)
       3103. Resultados Acumulados (Utilidades/Pérdidas retenidas)
       3104. Resultado del Ejercicio

4. COSTOS Y GASTOS (EXPENSES / DEBIT RESULTS)
   41. COSTOS Y GASTOS DE OPERACIÓN
       4101. Costo de Ventas
       4102. Gastos de Administración (Sueldos, alquileres, servicios)
       4103. Gastos de Venta (Comisiones, mercadeo)
       4104. Gastos Financieros (Intereses bancarios)

5. CUENTAS LIQUIDADORAS (CLOSING ACCOUNTS)
   5101. Pérdidas y Ganancias

6. INGRESOS (REVENUES / CREDIT RESULTS)
   61. INGRESOS DE OPERACIÓN
       6101. Ventas Locales Gravadas
       6102. Ventas Locales Exentas
       6103. Ventas de Exportación
   62. OTROS INGRESOS
```

---

## 2. Agent Usage Guidelines
When generating journal entries or balance sheets, always format account codes to at least 4 digits (Level 3 - Major Account) and 6 digits (Level 4 - Subaccount) to ensure direct importability into local ERPs (SAP, QuickBooks, CONTAPAQ, local Salvadoran systems).
