# Claude-Skills

A collection of custom Claude AI skill files that power a modular, end-to-end job application workflow — from resume auditing to cover letter generation and LinkedIn optimization.

---

## Workflows

### Resume & Cover Letter Pipeline

Run these skills in sequence for a fully tailored, submission-ready application:

| Step | Skill | What it does |
|------|-------|-------------|
| 1 | `jd-resume-auditor` | Audits your resume against a job description and produces a structured gap report |
| 2 | `context-gatherer` | Conducts a targeted interview to collect new information that closes identified gaps |
| 3 | `resume-formatter` | Rewrites and formats the final tailored resume as a submission-ready `.docx` |
| 4 | `cover-letter-writer` | Generates a 4-paragraph, job-specific cover letter as a `.docx` |

### LinkedIn Pipeline

Run these skills in sequence to audit and rewrite your LinkedIn profile:

| Step | Skill | What it does |
|------|-------|-------------|
| 1 | `linkedin-audit` | Benchmarks your existing LinkedIn profile and identifies positioning gaps |
| 2 | `linkedin-formatter` | Rewrites your profile into a copy-paste ready update |

### Standalone

| Skill | What it does |
|-------|-------------|
| `cv-formatter` | Produces a polished general-purpose CV from raw experience data as a `.docx` |

---

## Repository structure

```
Claude-Skills/
├── context-gatherer/
│   └── SKILL.md
├── cover-letter-writer/
│   └── SKILL.md
├── cv-formatter/
│   ├── SKILL.md
│   └── references/
│       └── template-spec.md     ← Formatting template used by the skill at runtime
├── jd-resume-auditor/
│   └── SKILL.md
├── linkedin-audit/
│   └── SKILL.md
├── linkedin-formatter/
│   └── SKILL.md
└── resume-formatter/
    ├── SKILL.md
    └── references/
        └── template-spec.md     ← Formatting template used by the skill at runtime
```

Each folder contains a `SKILL.md` file that Claude reads at runtime to execute that step. Skills marked with a `references/` subfolder include additional formatting specs that the skill pulls in during output generation.

---

## How to use

1. Copy the contents of any `SKILL.md` into a Claude Project's **custom instructions** field, or reference the file path directly in your workflow.
2. Start at Step 1 of the relevant pipeline and work through the steps in order.
3. Each skill's output feeds directly into the next step as input.
