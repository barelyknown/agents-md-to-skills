---
name: agents-md-to-skills
description: Convert AGENTS.md (or similar agent instruction docs) into reusable Codex skills. Use when asked to extract, split, or refactor AGENTS.md guidance into skill folders, or to create skills that replace sections of an AGENTS.md file.
---

# AGENTS.md to Skills

Turn long or mixed-purpose AGENTS.md guidance into focused, reusable skills that Codex can trigger automatically.

## Workflow

1. Locate the source instructions
   - Find the AGENTS.md (or equivalent) file in the repo.
   - Ask which sections to convert if it is unclear or if the file is long.

2. Identify skill candidates
   - Group content that describes a repeatable workflow, tool usage pattern, or domain-specific knowledge.
   - Keep global constraints (security, testing, coding style) in AGENTS.md unless they are truly task-specific.
   - Prefer small, single-responsibility skills.

3. Propose a skill map
   - For each candidate, propose a hyphen-case skill name and a one-line purpose.
   - Merge candidates only if they share the same trigger and steps.

4. Create each skill folder
   - Create `.codex/skills/<skill-name>/` in the target repo scope unless the user specifies another location.
   - Add `SKILL.md` with valid frontmatter (name + description only).

5. Write triggers and instructions
   - In `description`, include both what the skill does and when to use it (trigger phrases or contexts).
   - In the body, write imperative, step-by-step guidance.
   - Keep SKILL.md lean; move large reference material into `references/` and link from SKILL.md.
   - Avoid extra docs inside the skill (no README, changelog, or setup guides).

6. Update AGENTS.md
   - Replace converted sections with short pointers to the skill (e.g., “Use $skill-name for <task>”).
   - Keep only repository-wide rules and minimal navigation.

7. Validate
   - Ensure `name` matches the folder and uses lowercase letters, numbers, and hyphens only.
   - Keep `description` under 1024 characters and single-line.
   - If available, run `skills-ref validate` on the new skill folder(s).

## Heuristics for what to extract

Extract into a skill when the section:
- Describes a multi-step process or checklist.
- Documents a tool workflow, command sequence, or API usage.
- Encodes team-specific conventions for a repeatable task.
- Is large enough to distract from global, repo-wide rules.

Keep in AGENTS.md when the section:
- Defines global policies (security, testing, style).
- Applies to every task regardless of type.
- Is a short reminder that does not justify a new skill.

## SKILL.md template

```md
---
name: <skill-name>
description: <what it does + when to use it>
---

<imperative instructions>
```

## Output expectations

- New skill directories with valid `SKILL.md` files.
- AGENTS.md updated to reference the skills.
- A brief summary of changes and any follow-up questions.
