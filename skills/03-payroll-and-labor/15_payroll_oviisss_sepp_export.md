---
name: payroll-sv-oviisss-sepp-export
description: Formats, validates, and exports electronic payroll files for official government and pension portals in El Salvador (OVISSS for ISSS and SEPP for AFP Crecer/Confía).
version: 1.0.0
category: payroll-and-labor
jurisdiction: El Salvador (SV)
regulatory_references: [OVISSS Flat File Specifications; SEPP/SIP Standard File Layouts]
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama, DeepSeek]
---

# 👥 SKILL 15: OVISSS & SEPP/AFP Electronic File Generator

## 🎯 Purpose
Guide AI agents to transform calculated payroll registers into fixed-width text (`.txt`) and delimited files compliant with official Salvadoran state filing portals: **OVISSS** (ISSS Online) and **SEPP** (AFP Electronic Payroll System).

---

## 1. OVISSS (ISSS Electronic Payroll Layout)

The Social Security Institute requires a fixed-width ASCII text file without delimiters:

### Core Record Layout (Sample Fields):
1. **Patronal Number (Número Patronal):** 9 digits (padded with leading zeros).
2. **Declaration Year and Month:** `YYYYMM` (6 chars).
3. **Employee Identification:** DUI (9 digits without hyphens).
4. **Employee First & Last Name:** Fixed-width 40 characters (left-aligned, space-padded).
5. **Days Worked:** 2 digits (e.g. `30` or `15`).
6. **Reported Wage (Salario Devengado):** 8 digits, 2 implied decimals (e.g. \$1,200.00 becomes `00120000`).
7. **Labor Deduction (Cotización Empleado):** Implied decimals, capped at \$30.00 (`00003000`).
8. **Employer Contribution (Cotización Patronal):** Capped at \$75.00 (`00007500`).

---

## 2. SEPP / SIP (AFP Electronic Payroll Layout)

Pension Fund Administrators (Crecer & Confía) require fixed-length or CSV records structured as follows:

### Required Fields:
- NUP (Número Único Previsional): 12 numeric digits.
- Worker's DUI / NIT: Validated with check digit.
- Pension Fund Identifier: `01` (Crecer), `02` (Confía), or other SIP entity.
- Base Pensionable Salary: Total uncapped taxable wage.
- Employee Deduction (7.25%): 2 decimals.
- Employer Contribution (8.75%): 2 decimals.
- Special Movement Code: `00` (Normal active worker), `01` (New hire), `02` (Termination / Resignation), `03` (Medical leave).

---

## 3. Agent Validation Routine
Before presenting or downloading the generated file:
1. Verify that all DUIs are exactly 9 numeric digits.
2. Confirm that total records count matches payroll roster.
3. Sum the file's hash totals (total wages, total employee deductions, total employer contributions) and match against accounting ledger control balances.
