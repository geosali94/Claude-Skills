# Claude-Skills

A collection of custom Claude AI skill files built to power a modular, end-to-end job application workflow — from resume auditing to cover letter generation.

## What's in here

These skills are designed to work as a sequential pipeline inside Claude, each feeding into the next:

| Skill | Purpose |
|---|---|
| `jd-resume-auditor` | Audits a resume against a job description and produces a structured gap report |
| `context-gatherer` | Conducts a targeted interview to collect new information that closes identified gaps |
| `resume-formatter` | Rewrites and formats the final tailored resume as a submission-ready `.docx` |
| `cover-letter-writer` | Generates a 4-paragraph, job-specific cover letter as a `.docx` |
| `cv-formatter` | Produces a polished general-purpose CV from raw experience data |
| `linkedin-audit` | Benchmarks an existing LinkedIn profile and identifies positioning gaps |
| `linkedin-formatter` | Rewrites a LinkedIn profile into a copy-paste ready update |

## How to use

Each folder contains a `SKILL.md` file that Claude reads at runtime to execute that step. Some skills include a `references/` subfolder with formatting templates or specs.
