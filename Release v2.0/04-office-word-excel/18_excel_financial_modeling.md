---
name: kronos-excel-financial-model-openpyxl
description: Generates automated financial workbooks (.xlsx) with dynamic formulas (SUMIFS, XLOOKUP), number formatting, and frozen panes via openpyxl.
version: 1.0.0
category: office-word-excel
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📊 SKILL 18: Automated Excel Financial Modeling & OpenPyXL Engine

## 🎯 Purpose
Build audit-ready Microsoft Excel workbooks (`.xlsx`) containing dynamic native Excel formulas, explicit financial number formats, conditional formatting, and grid alignments.

## 🛠️ Execution Protocol
1. **Never Hardcode Calculations:** Write native Excel formula strings (`=SUM(C2:C50)`, `=XLOOKUP(...)`, `=SUMIFS(...)`) so the spreadsheet remains dynamic.
2. **Explicit Number Formatting:**
   - Currency: `"$#,##0.00"`
   - Percentages: `"0.00%"`
   - Dates: `"YYYY-MM-DD"`
3. **Workbook UX Standards:**
   - Freeze top header row (`ws.freeze_panes = "A2"`).
   - Auto-fit column widths with 3-character padding.
   - Dark theme header with white bold text.

```python
import openpyxl
from openpyxl.styles import Font, PatternFill, Alignment, numbers
from openpyxl.utils import get_column_letter

wb = openpyxl.Workbook()
ws = wb.active
ws.title = "VAT_Ledger"

headers = ["Voucher", "Date", "Taxable Base", "13% VAT", "Total"]
ws.append(headers)

# Styling
header_fill = PatternFill(start_color="1F4E79", end_color="1F4E79", fill_type="solid")
header_font = Font(name="Calibri", size=11, bold=True, color="FFFFFF")

for col in range(1, len(headers) + 1):
    cell = ws.cell(row=1, column=col)
    cell.fill = header_fill
    cell.font = header_font
    cell.alignment = Alignment(horizontal="center")

ws.freeze_panes = "A2"
wb.save("vat_ledger_output.xlsx")
```
