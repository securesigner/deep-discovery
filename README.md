# Deep Discovery

Deep Discovery is a Codex plugin that adds the `deep-discovery` skill for a
100-question self-interrogation process before committing to a design, plan, or
strategy.

It is designed for architecture review, code review, Codex plugin and skill
audits, business and product strategy, trading system evaluation, and general
problem exploration.

## Install

Register this repository as a Codex marketplace:

```powershell
codex plugin marketplace add forsonny/deep-discovery
```

If that command fails on Windows with a Git staging-path error, use a local
checkout:

```powershell
git clone https://github.com/forsonny/deep-discovery.git
cd deep-discovery
codex plugin marketplace add .
```

Restart Codex, open Plugins, switch the filter to show third-party plugins, and
install `deep-discovery` from `Deep Discovery Plugins`.

For a local checkout, run this from the repository root:

```powershell
codex plugin marketplace add .
```

To pick up repository updates later:

```powershell
codex plugin marketplace upgrade deep-discovery-marketplace
```

Codex currently exposes marketplace management in the CLI. The final plugin
install step happens in the Codex Plugins UI.

See [docs/README.codex.md](docs/README.codex.md) for the Codex-specific install
and verification notes.

## Usage

After installation, start a new Codex session and ask for Deep Discovery by name
or by intent:

```text
Run deep discovery on this architecture.
Stress test this plan with 100 questions.
Use deep-discovery to audit this Codex plugin before I publish it.
```

The skill routes to focused reference patterns for software architecture, code
review, Codex plugin and skill creation, business and product strategy, trading
and financial systems, or general analysis.

## Contents

| Path | Purpose |
|------|---------|
| `.codex-plugin/plugin.json` | Codex plugin manifest and interface metadata |
| `.agents/plugins/marketplace.json` | Repo marketplace manifest for Codex discovery |
| `skills/deep-discovery/SKILL.md` | Main skill instructions |
| `skills/deep-discovery/references/` | Domain-specific question patterns |
| `docs/README.codex.md` | Codex install and verification notes |

## Validate

From the repository root:

```powershell
python -m json.tool .codex-plugin\plugin.json
python -m json.tool .agents\plugins\marketplace.json
$codexHome = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME ".codex" }
$validator = Join-Path $codexHome "skills\.system\skill-creator\scripts\quick_validate.py"
python $validator skills\deep-discovery
```

The last command uses Codex's local `skill-creator` validator. If that validator
is not available, use Codex's current skill validation workflow.

## License

MIT. See [LICENSE](LICENSE).
