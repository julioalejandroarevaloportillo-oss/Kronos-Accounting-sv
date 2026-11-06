---
name: kronos-word-docx-generator
description: Generates executive Word documents (.docx) with cover pages, custom typography, corporate palettes, tables, and headers/footers via python-docx.
version: 1.0.0
category: office-word-excel
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📄 SKILL 16: Automated Executive Word Document (.docx) Generator

## 🎯 Purpose
Instruct AI agents to generate publication-grade Microsoft Word reports (`.docx`) using `python-docx` with custom brand palettes, formal typography, tables, and page geometry.

## 🛠️ Execution Protocol
1. **Document Geometry:** Set standard Letter/A4 page margins (1 inch / 2.54 cm all sides).
2. **Typography Hierarchy:**
   - Title: 24pt Bold (Primary brand color).
   - Heading 1: 18pt Bold with bottom accent border.
   - Heading 2: 14pt Semi-bold.
   - Body: 11pt Regular (Calibri, Aptos, or Arial), 1.15 line spacing, 6pt after.
3. **Table Styling:**
   - Shaded header row with white text.
   - Alternating zebra striping (`#F2F4F7`).
   - Explicit column widths and cell padding.
4. **Header & Footer:**
   - Header: Confidentiality disclaimer & document title.
   - Footer: Page number field (`Page X of Y`) and generation timestamp.

```python
from docx import Document
from docx.shared import Inches, Pt, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH

doc = Document()
for section in doc.sections:
    section.top_margin = Inches(1)
    section.bottom_margin = Inches(1)
    section.left_margin = Inches(1)
    section.right_margin = Inches(1)
```
