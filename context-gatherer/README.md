# context-gatherer

**Pipeline position:** Step 2 of 4 — Resume & Cover Letter Pipeline

## What it does

Takes the Gap Report from the JD Resume Auditor and conducts a targeted clarifying interview. It asks only the questions needed to close identified gaps — skipping anything already answered in your master Q&A document — and compiles the answers into a structured Context Document ready for the Resume Formatter.

## Inputs

- Gap Report from [`jd-resume-auditor`](../jd-resume-auditor/)
- (Optional) A master Q&A document with previously answered clarifying questions, used to avoid redundant prompts

## Output

A **Context Document** containing:
- New experience details, metrics, and examples gathered from the interview
- Clarified framing for gap areas identified in Step 1
- Structured notes organized to map directly into resume sections

## Next step

Feed the Context Document into [`resume-formatter`](../resume-formatter/) to produce the final tailored resume.
