# cv-formatter

**Pipeline position:** Standalone (not part of the sequential pipeline)

## What it does

Produces a polished, general-purpose CV from raw experience data. Unlike the resume-formatter (which tailors output to a specific job description), the CV formatter creates a comprehensive, evergreen document covering your full professional history, skills, and accomplishments.

## Inputs

- Raw experience data (work history, education, projects, skills — paste as text or provide existing CV)

## Output

A fully formatted **CV `.docx`** with:
- Bullet points rewritten using the **Accomplished [X] as measured by [Y] by doing [Z]** formula
- Consistent formatting matching the canonical CV template

> **Note:** The `references/` subfolder contains a `template-spec.md` that defines the exact formatting rules (fonts, spacing, section order, bullet style) used by this skill at runtime.

## When to use this vs. resume-formatter

Use `cv-formatter` for general applications, portfolio submissions, or when you need a comprehensive baseline document. Use `resume-formatter` when tailoring to a specific job description.
