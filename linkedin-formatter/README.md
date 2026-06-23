# linkedin-formatter

**Pipeline position:** Step 2 of 2 — LinkedIn Pipeline

## What it does

Takes the LinkedIn Audit Summary from the LinkedIn Audit and transforms it into a complete, copy-paste ready `LinkedIn-Update.md` file. Every section is rewritten with stronger positioning, outcome-driven bullets, and keyword alignment for recruiter discoverability.

## Inputs

- LinkedIn Audit Summary from [`linkedin-audit`](../linkedin-audit/)
- Resume (for metric and evidence sourcing)
- (Optional) GitHub profile or project portfolio

## Output

A **`LinkedIn-Update.md`** file containing ready-to-paste rewrites for:
- Headline
- About / Summary section
- All experience entries (with outcome + measurement + method bullets)
- Skills section recommendations
- Any additional sections identified during the audit

## Notes

This skill produces a Markdown file rather than a `.docx` because LinkedIn content is pasted directly into the platform's editor rather than uploaded as a document.
