# Deep Discovery on Claude Code

Targets Claude Code's plugin and skill conventions:

- `.claude-plugin/plugin.json` — plugin manifest.
- `.claude-plugin/marketplace.json` — marketplace manifest listing this plugin.
- `skills/deep-discovery/SKILL.md` — the skill (YAML frontmatter + body).
- `skills/deep-discovery/references/` — domain-specific question patterns.

## Install

There are two install paths. Pick whichever fits your workflow.

### A. Drop-in skill (simplest)

Copy the skill folder into your user-level skills directory:

```bash
mkdir -p ~/.claude/skills
cp -r skills/deep-discovery ~/.claude/skills/
```

Or, on Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse skills\deep-discovery "$HOME\.claude\skills\"
```

Open a fresh Claude Code session and trigger it with one of the prompts in
[Verify](#verify). No restart of the host process is required.

### B. As a plugin (via marketplace)

From any directory, register this repo as a marketplace and install the plugin:

```text
/plugin marketplace add forsonny/deep-discovery
/plugin install deep-discovery@deep-discovery
```

The `@deep-discovery` suffix names the marketplace (the `name` field in
`.claude-plugin/marketplace.json`). To pick up later updates:

```text
/plugin marketplace update
```

For a local checkout, point the marketplace at the repo root:

```text
/plugin marketplace add /absolute/path/to/deep-discovery
```

## Verify

Open a new Claude Code session and trigger the skill explicitly:

```text
Run deep discovery on this architecture.
Stress test this plan with 100 questions.
Use deep-discovery to audit this Claude Code plugin before I publish it.
```

Expected behavior:

- The `deep-discovery` skill activates and runs its preflight (mode and domain
  pattern selection).
- Q1 is always: *"What is the goal, and how do we get there?"*
- The run progresses through Foundation → Mechanics → Stress Testing →
  Competitive/Alternatives → Feasibility → Refinement → Synthesis without
  abbreviation.
- The final response summarizes top issues, top strengths, recommended changes,
  a revised proposal (when applicable), and a one-paragraph honest bottom line.

## Validate the manifests

Quick JSON sanity check from the repo root:

```bash
python -m json.tool .claude-plugin/plugin.json
python -m json.tool .claude-plugin/marketplace.json
```

## Files

- `../.claude-plugin/plugin.json` — plugin manifest
- `../.claude-plugin/marketplace.json` — marketplace manifest
- `../skills/deep-discovery/SKILL.md` — main skill file
- `../skills/deep-discovery/references/` — domain-specific reference patterns
