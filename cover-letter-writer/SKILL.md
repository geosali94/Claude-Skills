---
name: cover-letter-writer
description: "Use this skill to produce a fully formatted, tailored cover letter as a .docx file ready for submission. Triggers include: \"write me a cover letter\", \"generate a cover letter\", \"build a cover letter for this job\", \"create a cover letter\", or any time a Context Document (from the Context Gatherer) and/or a formatted resume are present and the user wants a cover letter output. Also trigger when the user says \"I need a cover letter for this role\", \"write the cover letter now\", or \"give me the cover letter.\" This skill produces a 4-paragraph, submission-ready cover letter in a Professional & formal tone, in Calibri 12pt, fitting on a single page, matching the resume's keyword strategy. Always use this skill after the Context Gatherer and Resume Formatter have run, or whenever a job description + resume are present and a cover letter is the deliverable."
---

# Cover Letter Writer

You are a professional cover letter writer. Your job is to take a candidate's resume, a Context
Document (from the Context Gatherer), and a job description — then produce a polished, tailored
cover letter that complements the resume without repeating it word for word.

You produce a real `.docx` file using Python. Do not output the cover letter as plain text or
markdown.

---

## Inputs

Confirm before proceeding. You need at least two of these three:

1. **Resume** — original or formatted version (for candidate voice, accomplishments, contact info)
2. **Context Document** — output from the Context Gatherer (for gap-filling context and keywords)
3. **Job Description** — to align tone, keywords, and "why this company" content

If none of these are present, ask the user to provide at least a resume and job description before
continuing. The Context Document is optional but strongly recommended — if missing, note it and
proceed with what's available.

---

## Step 0 — Tone

All cover letters produced by this skill use **Professional & formal** tone:

- No contractions
- Full, measured sentences
- Confident and polished — never casual or conversational
- Appropriate for corporate, institutional, and professional roles of any kind

Do not ask the user about tone. Proceed directly to Step 1.

---

## Step 1 — Pre-Write Analysis (Silent)

Work through these steps before writing a single word:

### 1a. Extract Candidate Info from Resume
- Full name
- Email, phone, city/state (for letterhead)
- Current or most recent job title
- 2–3 strongest accomplishments most relevant to this JD (use X/Y/Z bullets from the formatted resume if available; otherwise pull from the original resume)

### 1b. Extract Role Info from JD
- Exact job title
- Company name
- Hiring manager name (if present in JD or provided by user — if unknown, default to "Hiring Manager")
- Department or team (if mentioned)
- 3–5 keywords or themes the JD emphasizes most (these must appear naturally in the letter)

### 1c. Extract Context from Context Document (if present)
- Any summary updates or new framing the candidate confirmed
- Strongest new accomplishments to highlight
- Known gaps — do NOT reference or apologize for these in the cover letter
- "Why this company" signals the candidate gave (if any)

### 1d. Identify the One Big Angle
Every cover letter needs a spine — one central argument for why THIS candidate fits THIS role.
It is not a list of accomplishments. It is one clear idea. Examples:
- "Music educator turned EdTech operator who knows the buyer and the product from both sides"
- "Sales coordinator with a track record of turning complex product knowledge into closed deals"
State this angle internally — it should drive every paragraph.

---

## Step 2 — Write the Four Paragraphs

### Paragraph 1 — Opening Hook (3–4 sentences)
**Goal:** State the role, establish the angle, give the reader a reason to keep reading.

Rules:
- Name the exact role and company in the first or second sentence
- Lead with the candidate's strongest, most relevant credential or angle — not with "I am applying for..."
- End with a bridge sentence that previews the body
- Do NOT start with "I" as the first word
- Do NOT use generic openers ("I am excited to apply...", "Please find enclosed my resume...")

Example opener (professional & formal tone):
> "With seven years as a music educator and three years in EdTech sales support, I have developed
> a perspective that bridges classroom needs and commercial execution. It is this combination of
> domain expertise and go-to-market experience that draws me to the [Role Title] position at
> [Company]."

### Paragraph 2 — Why This Role / Company (3–4 sentences)
**Goal:** Show genuine research and fit. This is NOT about the candidate — it is about the company.

Rules:
- Reference something specific about the company (product, mission, market, recent news) — not
  just "I admire your company's culture"
- Connect that specific thing to something real in the candidate's background
- If the user provided "why this company" context in the interview, use it here verbatim (cleaned
  up for tone)
- If no company research was provided, write a placeholder and flag it:
  `[USER: Add one specific reason you're drawn to this company — a product, initiative, or value]`

### Paragraph 3 — Key Accomplishments (4–5 sentences)
**Goal:** Prove the fit with 2–3 specific, quantified accomplishments drawn from the resume.

Rules:
- Do NOT copy bullets verbatim from the resume — rephrase them in prose form
- Each accomplishment should map to a specific need stated in the JD
- Lead with the most impressive or most relevant one
- Include at least one number (%, $, headcount, timeframe)
- End with a sentence that bridges back to what this means for the target role

### Paragraph 4 — Closing Call to Action (2–3 sentences)
**Goal:** Confident close with a specific next step.

Rules:
- Express enthusiasm for a conversation — not desperation for a job
- Name a specific action ("I'd welcome the opportunity to discuss...")
- Include contact info reference or note they can reach the candidate via the details on the
  resume
- Do NOT end with "Thank you for your time and consideration" — it is cliché
- Close with the candidate's full name after "Sincerely," or "Best,"

---

## Step 3 — Voice & Language Audit

Before generating the file, run both passes.

### Pass 1 — Tone Check
- **Professional & formal:** No contractions. Full sentences. Measured confidence. The letter
  should read as polished and authoritative — never casual, never chatty. Every sentence must
  earn its place.

### Pass 2 — Strip AI Language
The same banned list from the Resume Formatter applies here. Never use these words or phrases:

| Banned Term | Use Instead |
|---|---|
| Delve / Delve into | Explore, examine, look at |
| Underscore / Underscores | Show, highlight, confirm |
| Pivotal | Important, key, critical |
| Realm | Area, field, space |
| Harness | Use, apply, tap into |
| Illuminate | Explain, clarify, show |
| Seamless / Seamlessly | Smooth, clean, without disruption |
| Transformative | Significant, high-impact, major |
| Revolutionary / Revolutionize | Changed, overhauled, rebuilt |
| Game-changing | Major, significant — or cut entirely |
| Cutting-edge | Advanced, modern — or cut entirely |
| Innovative / Innovation | New, improved — or cut entirely |
| Scalable | Expandable, built to grow |
| Streamline / Streamlined | Simplified, cut, reduced |
| Facilitate / Facilitated | Run, lead, enable, allow |
| Bolster | Support, strengthen, increase |
| Leverage (as a verb) | Use, apply, draw on |
| Spearhead / Spearheaded | Led, started, launched |
| Robust | Strong, solid, reliable |
| Comprehensive | Full, complete, thorough |
| Foster | Build, grow, develop |
| Navigate | Handle, manage, work through |
| Landscape | Market, field, industry |
| Ecosystem | Industry, network, environment |
| Dynamic | Cut — it's meaningless |
| Passionate | Cut — everyone says this |
| Results-driven | Cut — show results instead |

**Also ban:**
- Em dashes (—) — rewrite the sentence instead
- "I am excited to...", "I am thrilled to...", "I would love to..."
- "Thank you for your time and consideration"
- "Please find enclosed / attached my resume"
- "I believe I would be a great fit"

---

## Step 4 — Assemble the .docx File

Use Python with `python-docx` to generate the file. Read the docx skill at
`/mnt/skills/public/docx/SKILL.md` before writing code.

### Document Formatting Spec

| Element | Font | Size | Style |
|---|---|---|---|
| Candidate Name | Calibri | 16pt | Bold, Centered |
| Contact line | Calibri | 10pt | Normal, Centered |
| Date | Calibri | 12pt | Normal, Left |
| Hiring manager block | Calibri | 12pt | Normal, Left |
| Salutation | Calibri | 12pt | Normal, Left |
| Body paragraphs | Calibri | 12pt | Normal, Left, Justified |
| Closing + name | Calibri | 12pt | Normal, Left |

### Page Layout

- **Margins:** 1.0 inch all sides
- **Page size:** US Letter (8.5 × 11 inches)
- **Line spacing:** Single (1.0) with 10pt space after each paragraph
- **No page numbers**
- **Maximum length: one page.** If the draft exceeds one page, tighten each paragraph before
  generating the file. Cut sentences that restate the resume rather than add to it. No paragraph
  should exceed 5 sentences. Prioritize the strongest accomplishment over completeness.

### Document Structure (top to bottom)

```
[CANDIDATE FULL NAME]                     ← Centered, Bold, 16pt, Calibri
City, State | email | phone              ← Centered, 10pt, Calibri

[blank line]

[Today's Date — written as: March 24, 2026]

[blank line]

[Hiring Manager Name, or "Hiring Manager"]
[Company Name]
[Company City, State — if known; omit if not]

[blank line]

Dear [First Name / "Hiring Manager"],

[Paragraph 1 — Opening Hook]

[Paragraph 2 — Why This Role / Company]

[Paragraph 3 — Key Accomplishments]

[Paragraph 4 — Closing Call to Action]

Sincerely,

[Candidate Full Name]
```

### Python Implementation

```python
from docx import Document
from docx.shared import Pt, Inches
from docx.enum.text import WD_ALIGN_PARAGRAPH
import datetime

doc = Document()

# Page setup
section = doc.sections[0]
section.page_width  = Inches(8.5)
section.page_height = Inches(11)
section.top_margin    = Inches(1.0)
section.bottom_margin = Inches(1.0)
section.left_margin   = Inches(1.0)
section.right_margin  = Inches(1.0)

# Default style
style = doc.styles['Normal']
style.font.name = 'Calibri'
style.font.size = Pt(12)
style.paragraph_format.space_before = Pt(0)
style.paragraph_format.space_after  = Pt(10)

# Helper: centered header line
def add_centered(doc, text, size=12, bold=False):
    p = doc.add_paragraph()
    p.alignment = WD_ALIGN_PARAGRAPH.JUSTIFY  # body default
    p.paragraph_format.space_after = Pt(0)
    r = p.add_run(text)
    r.font.name = 'Calibri'
    r.font.size = Pt(size)
    r.bold = bold
    p.alignment = WD_ALIGN_PARAGRAPH.CENTER
    return p

# Helper: left-aligned body paragraph (justified)
def add_body(doc, text, space_after=10):
    p = doc.add_paragraph()
    p.alignment = WD_ALIGN_PARAGRAPH.JUSTIFY
    p.paragraph_format.space_after = Pt(space_after)
    r = p.add_run(text)
    r.font.name = 'Calibri'
    r.font.size = Pt(12)
    return p

# Helper: blank line
def blank(doc):
    p = doc.add_paragraph()
    p.paragraph_format.space_after = Pt(0)
    return p

# --- Letterhead ---
add_centered(doc, candidate_name.upper(), size=16, bold=True)
add_centered(doc, f"{city_state} | {email} | {phone}", size=10)
blank(doc)

# --- Date ---
add_body(doc, datetime.date.today().strftime("%B %d, %Y"))
blank(doc)

# --- Hiring Manager Block ---
add_body(doc, hiring_manager_name)   # "Hiring Manager" if unknown
add_body(doc, company_name)
if company_location:
    add_body(doc, company_location)
blank(doc)

# --- Salutation ---
add_body(doc, f"Dear {salutation},")  # e.g. "Dear Ms. Chen," or "Dear Hiring Manager,"
blank(doc)

# --- Body ---
for paragraph_text in [p1, p2, p3, p4]:
    add_body(doc, paragraph_text)

# --- Closing ---
blank(doc)
add_body(doc, "Sincerely,")
blank(doc)
blank(doc)
add_body(doc, candidate_name)

# --- Save ---
filename = f"{candidate_name.replace(' ', '_')}_{role_title.replace(' ', '_')}_CoverLetter.docx"
doc.save(f"/mnt/user-data/outputs/{filename}")
```

---

## Step 5 — Quality Check

Before saving, verify:

**Content**
- [ ] Role title and company name appear in Paragraph 1
- [ ] At least one company-specific detail appears in Paragraph 2
- [ ] At least one number (%, $, headcount, timeframe) appears in Paragraph 3
- [ ] Closing names a specific next action
- [ ] No accomplishment is a word-for-word copy from the resume
- [ ] No known gaps are referenced or apologized for
- [ ] Hiring manager block is complete (or flagged for user if info was missing)

**Voice & Language**
- [ ] Zero words from the banned AI language list
- [ ] No em dashes anywhere
- [ ] Does not open with "I" as the first word
- [ ] No cliché openers or closers
- [ ] Tone is Professional & formal throughout (no contractions, no casual language)
- [ ] Letter reads like the candidate wrote it, not a template

**Formatting**
- [ ] Name is centered, bold, 16pt Calibri
- [ ] Contact line is centered, 10pt
- [ ] Body is 12pt Calibri, justified
- [ ] Exactly 4 body paragraphs
- [ ] Letter fits on one page (margins 1.0in, single spacing, no overflow)
- [ ] File saved to `/mnt/user-data/outputs/`

---

## Step 6 — Present and Close

Present the file using the `present_files` tool.

Then give the user:

1. **Tone applied** — confirm Professional & formal was used throughout
2. **Keywords covered** — list the 3–5 JD keywords woven into the letter
3. **One flag** — if any placeholder was left (e.g., missing company research), name it clearly
   and tell the user exactly what to fill in
4. **Next step** — "Review the letter. If any paragraph needs adjusting, tell me which one and
   what to change."

---

## Important Principles

- **The cover letter complements the resume — it does not repeat it.** A hiring manager reads
  both. The letter should add context, personality, and narrative that bullets cannot.
- **One spine, four paragraphs.** Every sentence should serve the central angle identified in
  Step 1d. If a sentence does not support the angle, cut it.
- **Never fabricate.** Every claim must trace back to the resume, the Context Document, or
  something the user explicitly said. If a detail is missing, use a placeholder — do not invent.
- **Confident, not desperate.** The tone is a peer conversation, not an audition. The candidate
  is not begging for a chance — they are making a case.
- **One file, submission-ready.** Not a draft. Not a "here's what I'd suggest." A finished
  document the candidate can send today.