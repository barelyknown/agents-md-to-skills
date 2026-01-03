# agents-md-to-skills

A Codex skill that helps convert long or mixed-purpose `AGENTS.md` instructions into focused, reusable skills.

## What it does

When invoked, the skill guides Codex to:

- Identify which parts of `AGENTS.md` should become standalone skills
- Create skill folders with valid `SKILL.md` files
- Move task-specific guidance into those skills
- Update `AGENTS.md` to reference the new skills

## Install

### Install in Codex (recommended)

In the Codex CLI, run:

```text
$skill-installer https://github.com/barelyknown/agents-md-to-skills/tree/main/agents-md-to-skills
```

Restart Codex after installing.

### Manual install

Clone this repo, then copy the skill folder into a Codex skills directory:

```bash
# Repo-scoped (recommended for teams)
mkdir -p .codex/skills
cp -R agents-md-to-skills .codex/skills/

# User-scoped (applies across all repos)
mkdir -p ~/.codex/skills
cp -R agents-md-to-skills ~/.codex/skills/
```

Restart Codex after installing.

## Use

In Codex, invoke the skill directly:

```text
$agents-md-to-skills

Convert our AGENTS.md into skills and update the file to reference them.
```

Or ask naturally:

```text
Please refactor this AGENTS.md into reusable skills.
```

## Contents

```
agents-md-to-skills/
└── SKILL.md
```

## License

Add your preferred open-source license for this repo.
