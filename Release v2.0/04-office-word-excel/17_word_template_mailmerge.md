---
name: kronos-word-template-mailmerge
description: Injects structured JSON records into pre-designed Word (.docx) templates using python-docx-template (Jinja2 syntax) for automated contracts, invoices, and certificates.
version: 1.0.0
category: office-word-excel
compatible_models: [ChatGPT, Claude, Gemini, Antigravity, Cursor, Ollama]
---

# 📄 SKILL 17: Word Template Population & Mail Merge (docxtpl)

## 🎯 Purpose
Automate mass generation of legal contracts, employment agreements, DTE invoice representations, and certifications by populating Word templates containing Jinja2 tags.

## 🛠️ Execution Protocol
1. **Template Preparation:** Insert Jinja2 placeholders into the master `.docx`:
   - Simple variables: `{{ client_name }}`, `{{ nit }}`.
   - Conditionals: `{% if is_large_taxpayer %}...{% endif %}`.
   - Dynamic loops: `{% for item in items %}...{% endfor %}`.
2. **Python Render Script:**
```python
from docxtpl import DocxTemplate
from datetime import datetime

doc = DocxTemplate("master_contract_template.docx")
context = {
    "company_name": "KRONOS INVERSIONES S.A. DE C.V.",
    "effective_date": datetime.now().strftime("%Y-%m-%d"),
    "contract_value": 15000.00,
    "clauses": [
        "Confidentiality under Salvadoran Law",
        "Dispute resolution via San Salvador Arbitration"
    ]
}
doc.render(context)
doc.save("generated_contract_001.docx")
```
3. **Format Integrity:** Ensure styles, font colors, and table structures inside loops remain intact across iterations.
