# resume-formatter

**Pipeline position:** Step 3 of 4 — Resume & Cover Letter Pipeline

## What it does

Takes the Context Document from the Context Gatherer and rewrites your resume into a fully tailored, submission-ready `.docx` file. Every bullet point is rewritten using the **Accomplished [X] as measured by [Y] by doing [Z]** formula, and all new context is slotted into the correct template sections.

## Inputs

- Context Document from [`context-gatherer`](../context-gatherer/)
- Base resume (for sections not being rewritten)

## Output

A polished, tailored **resume `.docx`** matching the canonical resume template, formatted for ATS compatibility and recruiter readability.

> **Note:** The `references/` subfolder contains a `template-spec.md` that defines the exact formatting rules (fonts, spacing, section order, bullet style) used by this skill at runtime.

## Next step

Feed the formatted resume into [`cover-letter-writer`](../cover-letter-writer/) to generate a matching cover letter.
