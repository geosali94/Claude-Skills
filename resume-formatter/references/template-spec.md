# Resume Template Specification
# Reference file for Resume Formatter (Skill 3)
# Read this file before generating any .docx output.

---

## Visual Layout Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                        CANDIDATE NAME                           │  ← Centered, Bold, 16pt
│         City, State | email | phone | linkedin.com/in/handle    │  ← Centered, 10pt
├─────────────────────────────────────────────────────────────────┤
│ SUMMARY                                                         │  ← Bold, 11pt, underline rule below
│   • Factual intro bullet [scope + years]                        │
│   • Relevant accomplishment 1                                   │
│   • Relevant accomplishment 2                                   │
│   • Relevant accomplishment 3 (optional)                        │
├─────────────────────────────────────────────────────────────────┤
│ Technical Skills: Tool1, Tool2, Tool3, Tool4                    │  ← "Technical Skills:" bold, rest normal
├─────────────────────────────────────────────────────────────────┤
│ PROFESSIONAL EXPERIENCE                                         │  ← Bold, 11pt, underline rule below
│                                                                 │
│ Company Name                          Location (City, ST/Remote)│  ← Company bold left | Location right
│ Job Title                                  Mon YYYY – Mon YYYY  │  ← Title bold left | Dates right
│ Company summary in italics, 1–2 sentences describing            │
│ what the company does, size, and scale.                         │
│                                                                 │
│   • Accomplishment bullet (X/Y/Z formula)                       │
│   • Accomplishment bullet (X/Y/Z formula)                       │
│   • Accomplishment bullet (X/Y/Z formula)                       │
│   • Accomplishment bullet (X/Y/Z formula)                       │
│                                                                 │
│ [Repeat for each role]                                          │
├─────────────────────────────────────────────────────────────────┤
│ EDUCATION                                                       │  ← Bold, 11pt, underline rule below
│ Degree / Certification Name               YYYY                  │  ← Bold left | Year right
│ Institution Name — Classification/Honors                        │  ← Normal, left
└─────────────────────────────────────────────────────────────────┘
```

---

## Typography

| Element | Font | Size | Style |
|---|---|---|---|
| Candidate Name | Calibri (or Arial) | 16pt | Bold, Centered |
| Contact Line | Calibri | 10pt | Normal, Centered |
| Section Headers (SUMMARY, EXPERIENCE, etc.) | Calibri | 11pt | Bold, All Caps |
| Company Name | Calibri | 11pt | Bold |
| Job Title | Calibri | 11pt | Bold |
| Date / Location (right-aligned) | Calibri | 10pt | Normal |
| Company Summary | Calibri | 10pt | Italic |
| Bullet Points | Calibri | 10.5pt | Normal |
| Technical Skills label | Calibri | 10.5pt | Bold inline |
| Technical Skills values | Calibri | 10.5pt | Normal inline |
| Education Degree | Calibri | 10.5pt | Bold |
| Education Institution | Calibri | 10.5pt | Normal |

---

## Page Layout

- **Margins:** 0.75 inches all sides (top, bottom, left, right)
- **Page size:** US Letter (8.5 × 11 inches)
- **Line spacing:** Single (1.0) within sections; 6pt space after each paragraph/bullet
- **Space between sections:** 10pt before section header
- **No page numbers**

---

## Section Rules

### #1 — Header

```
[CANDIDATE FULL NAME]                          ← centered, bold, 16pt, all caps or title case
City, State | email@domain.com | 555-123-4567 | linkedin.com/in/handle
```

- Single line for contact info, pipe ( | ) as separator
- No icons, no labels ("Email:", "Phone:" etc.) — just the values
- LinkedIn URL: use the short form `linkedin.com/in/handle` not full https://

---

### #2 & #3 — Summary Section

Header: `SUMMARY` — bold, all caps, followed immediately by a thin horizontal line rule

Bullets:
- **First bullet (#2):** Factual intro. States years of experience, type of work, scope.
  Example: "7 years in music education and EdTech, leading band programs of 150+ students
  and managing curriculum adoption across 6A competitive districts in Texas."
  - Do NOT start with "I"
  - Do NOT use subjective language ("passionate", "dynamic", "results-driven")
  - Factual, third-person implied

- **Remaining bullets (#3):** 2–3 relevant accomplishments tailored to THIS job.
  These change with every application. Pull from Context Document SUMMARY SECTION UPDATES.
  Each should be 1–2 lines, achievement-oriented, quantified where possible.

**Total Summary bullets: 3–4 max.** No walls of text.

---

### #4 — Technical Skills Line

```
Technical Skills: Tool1, Tool2, Tool3, Tool4, Tool5.
```

- Single line (not a bulleted list)
- "Technical Skills:" in bold, remainder in normal weight
- Comma-separated, period at end
- Include tools from original resume + any new tools confirmed in Context Document
- Order: Most JD-relevant first

---

### #5 & #6 — Professional Experience Entries

Header: `PROFESSIONAL EXPERIENCE` — bold, all caps, thin horizontal line rule below

Each role follows this exact structure:

**Line 1 (Company + Location):**
```
Company Name                                           City, ST / Remote
```
- Company name: bold, left-aligned
- Location: normal weight, right-aligned on same line
- Use tab stop or right-aligned text for location

**Line 2 (Title + Dates):**
```
Job Title                                           Mon YYYY – Mon YYYY
```
- Job title: bold, left-aligned
- Dates: normal weight, right-aligned on same line
- Date format: `Nov 2018 – Apr 2022` (abbreviated month, en-dash, no extra spaces)
- If current role: `Jan 2023 – Present`

**Line 3 (Company Summary):**
- 1–2 sentences, italic, normal weight
- Describes: what the company does, size/scale, relevant context
- Example: *"Babylon was a global B2C + B2B digital healthcare and AI startup. At its peak,
  with 2,000+ employees, \$1.1B+ in revenue, its app and services covered 24 million
  beneficiaries in 15 countries."*
- Keep factual — not a place to brag. Sets context for the bullets that follow.

**Lines 4+ (Accomplishment Bullets):**
- 3–6 bullets per role
- All use X/Y/Z formula (see SKILL.md Step 2)
- Bullet character: standard round bullet (•)
- Indent: 0.25 inches from left margin
- Most JD-relevant bullets come first within each role

---

### #7 — Education Section

Header: `EDUCATION` — bold, all caps, thin horizontal line rule below

Each entry:
```
Degree Name or Certification                                         YYYY
Institution Name — Honors / Classification (if applicable)
```

- Degree/cert: bold, left-aligned
- Year: normal, right-aligned on same line
- Institution: normal weight, left-aligned on next line
- If honors or classification (First Class, Dean's List, etc.): append after em-dash on same line as institution

---

## Python-docx Implementation Notes

```python
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
from docx.oxml import OxmlElement
import copy

# Page setup
doc = Document()
section = doc.sections[0]
section.page_width  = Inches(8.5)
section.page_height = Inches(11)
section.top_margin    = Inches(0.75)
section.bottom_margin = Inches(0.75)
section.left_margin   = Inches(0.75)
section.right_margin  = Inches(0.75)

# Default paragraph spacing
from docx.shared import Pt
style = doc.styles['Normal']
style.font.name = 'Calibri'
style.font.size = Pt(10.5)
pf = style.paragraph_format
pf.space_before = Pt(0)
pf.space_after  = Pt(4)

# Helper: add horizontal rule after section header
def add_horizontal_rule(paragraph):
    p = paragraph._p
    pPr = p.get_or_add_pPr()
    pBdr = OxmlElement('w:pBdr')
    bottom = OxmlElement('w:bottom')
    bottom.set(qn('w:val'), 'single')
    bottom.set(qn('w:sz'), '6')
    bottom.set(qn('w:space'), '1')
    bottom.set(qn('w:color'), '000000')
    pBdr.append(bottom)
    pPr.append(pBdr)

# Helper: company/title line with right-aligned date or location
def add_two_col_line(doc, left_text, right_text, left_bold=True, font_size=10.5):
    para = doc.add_paragraph()
    para.paragraph_format.space_after = Pt(1)
    # Tab stop at right margin
    from docx.oxml.ns import qn
    from docx.oxml import OxmlElement
    pPr = para._p.get_or_add_pPr()
    tabs = OxmlElement('w:tabs')
    tab = OxmlElement('w:tab')
    tab.set(qn('w:val'), 'right')
    # 9 inches from left edge of page accounting for margins = 7.0 inches usable
    tab.set(qn('w:pos'), '9072')  # 9072 twips = 6.3 inches (usable width at 0.75in margins)
    tabs.append(tab)
    pPr.append(tabs)
    # Left run
    run_left = para.add_run(left_text)
    run_left.bold = left_bold
    run_left.font.size = Pt(font_size)
    # Tab + right run
    run_tab = para.add_run('\t')
    run_right = para.add_run(right_text)
    run_right.bold = False
    run_right.font.size = Pt(font_size - 0.5)
    return para

# Helper: section header with rule
def add_section_header(doc, title):
    para = doc.add_paragraph()
    para.paragraph_format.space_before = Pt(8)
    para.paragraph_format.space_after  = Pt(2)
    run = para.add_run(title)
    run.bold = True
    run.font.size = Pt(11)
    add_horizontal_rule(para)
    return para

# Helper: italic company summary
def add_company_summary(doc, text):
    para = doc.add_paragraph()
    para.paragraph_format.space_after = Pt(4)
    run = para.add_run(text)
    run.italic = True
    run.font.size = Pt(10)
    return para

# Helper: accomplishment bullet
def add_bullet(doc, text):
    para = doc.add_paragraph(style='List Bullet')
    para.paragraph_format.left_indent  = Inches(0.25)
    para.paragraph_format.space_after  = Pt(3)
    run = para.add_run(text)
    run.font.size = Pt(10.5)
    return para
```

**Full assembly order in code:**
1. Name (centered, bold, 16pt)
2. Contact line (centered, 10pt)
3. `add_section_header(doc, "SUMMARY")`
4. Summary bullets via `add_bullet()`
5. Technical Skills line (inline bold label + normal text)
6. `add_section_header(doc, "PROFESSIONAL EXPERIENCE")`
7. For each role: `add_two_col_line()` × 2 + `add_company_summary()` + `add_bullet()` × N
8. `add_section_header(doc, "EDUCATION")`
9. For each entry: `add_two_col_line()` + institution line

**Save:**
```python
filename = f"{candidate_name.replace(' ', '_')}_{role_title.replace(' ', '_')}_Resume.docx"
doc.save(f"/mnt/user-data/outputs/{filename}")
```
