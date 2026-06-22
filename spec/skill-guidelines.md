# dlut-skills Guidelines

## Skill Shape

Each skill lives in `skills/<skill-name>/` and must include:

```text
skills/<skill-name>/
└── SKILL.md
```

Optional supporting folders:

```text
skills/<skill-name>/
├── assets/
├── references/
└── scripts/
```

## SKILL.md Frontmatter

Use only:

```yaml
---
name: skill-name
description: Describe what the skill does and when to use it.
---
```

The `description` is the discovery surface. Include likely trigger phrases and boundaries there.

## Writing Rules

- Write for another Agent, not for an end user.
- Prefer short workflows, checklists, and decision rules.
- Keep campus-specific assumptions explicit.
- Mark time-sensitive facts and require fresh verification.
- Do not include private, copyrighted, or course-restricted material unless you have permission.

## Resource Rules

- `references/`: policies, schemas, examples, rubrics, domain notes, long instructions.
- `scripts/`: repeatable local automation. Include usage examples in `SKILL.md`.
- `assets/`: templates, images, sample files, boilerplate, and other reusable artifacts.

## Review Checklist

- The skill name is lowercase kebab-case.
- `description` says both what the skill does and when to use it.
- `SKILL.md` is scoped to one job.
- Long material is moved out of `SKILL.md`.
- Sensitive or private data is not included.
- Any script has a clear input, output, and validation path.
