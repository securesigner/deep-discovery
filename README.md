# Deep Discovery

Deep Discovery is a Claude Code plugin that adds the `deep-discovery` skill for
a 100-question self-interrogation process before committing to a design, plan,
or strategy.

It is designed for architecture review, code review, Claude Code plugin and
skill audits, business and product strategy, trading system evaluation, and
general problem exploration.

## Install

Two install paths — pick whichever fits.

### A. Drop-in skill (simplest)

Copy the skill folder into your user-level skills directory:

```bash
mkdir -p ~/.claude/skills
cp -r skills/deep-discovery ~/.claude/skills/
```

Open a fresh Claude Code session and trigger it. No host restart required.

### B. As a plugin (via marketplace)

```text
/plugin marketplace add forsonny/deep-discovery
/plugin install deep-discovery@deep-discovery
```

For a local checkout, point the marketplace at the repo root:

```text
/plugin marketplace add /absolute/path/to/deep-discovery
```

To pick up updates later:

```text
/plugin marketplace update
```

See [docs/README.claude.md](docs/README.claude.md) for the full Claude Code
install and verification notes.

## Usage

After installation, start a new Claude Code session and ask for Deep Discovery
by name or by intent:

```text
Run deep discovery on this architecture.
Stress test this plan with 100 questions.
Use deep-discovery to audit this Claude Code plugin before I publish it.
```

The skill routes to focused reference patterns for software architecture, code
review, Claude Code plugin and skill creation, business and product strategy,
trading and financial systems, or general analysis.

## Contents

| Path | Purpose |
|------|---------|
| `.claude-plugin/plugin.json` | Claude Code plugin manifest |
| `.claude-plugin/marketplace.json` | Claude Code marketplace manifest |
| `skills/deep-discovery/SKILL.md` | Main skill instructions |
| `skills/deep-discovery/references/` | Domain-specific question patterns |
| `docs/README.claude.md` | Claude Code install and verification notes |

## Validate

Quick JSON sanity check from the repo root:

```bash
python -m json.tool .claude-plugin/plugin.json
python -m json.tool .claude-plugin/marketplace.json
```

## License

MIT. See [LICENSE](LICENSE).
