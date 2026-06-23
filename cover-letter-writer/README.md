# cover-letter-writer

**Pipeline position:** Step 4 of 4 — Resume & Cover Letter Pipeline

## What it does

Generates a tailored, 4-paragraph cover letter as a submission-ready `.docx` file. The letter is written in a professional and formal tone, uses Calibri 12pt, fits on a single page, and mirrors the keyword strategy of the formatted resume produced in Step 3.

## Inputs

- Formatted resume from [`resume-formatter`](../resume-formatter/)
- Context Document from [`context-gatherer`](../context-gatherer/)
- Job description (used to align tone and keywords)

## Output

A **cover letter `.docx`** structured as:
1. Opening — role, source, and a strong hook
2. Relevant experience — most compelling match to the JD
3. Value add — what you bring beyond the minimum requirements
4. Closing — call to action and next steps

## Notes

Tone is locked to **Professional & Formal** as a non-negotiable default. This skill is the final deliverable step of the Resume & Cover Letter Pipeline.
