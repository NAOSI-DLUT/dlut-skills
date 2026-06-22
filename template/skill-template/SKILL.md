---
name: skill-template
description: Replace with a clear description of what this skill does and when Codex, Claude Code, or another agent should use it. Include concrete triggers such as user phrases, file types, campus workflows, or course tasks.
---

# Skill Template

## Goal

Describe the specific DLUT campus, course, document, or analysis workflow this skill helps with.

## Inputs

- List the information the user should provide.
- List files or data the agent should inspect.
- State any assumptions that must be confirmed.

## Workflow

1. Understand the user's concrete task and identify the expected output.
2. Check whether any campus policy, course requirement, date, or source material needs fresh verification.
3. Load only the relevant files from `references/`, `scripts/`, or `assets/`.
4. Produce the requested artifact or analysis.
5. Verify the output against the user's requirements and any course/campus constraints.

## Resources

- `references/`: Put long background notes, examples, rubrics, policies, or schemas here.
- `scripts/`: Put reusable deterministic scripts here.
- `assets/`: Put templates, images, sample files, or boilerplate here.

## Output

Describe the expected output format, such as a Markdown report, `.docx` draft, spreadsheet, chart, checklist, script result, or concise answer.

## Quality Rules

- Keep user privacy and course integrity first.
- Do not invent DLUT policies, deadlines, course rules, or system behavior.
- For time-sensitive information, ask the agent to verify against the latest official or user-provided source.
- When working with course assignments, help with understanding, planning, checking, and explanation; do not fabricate results or bypass academic requirements.
