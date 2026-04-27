# Deep Discovery on Codex

Verified locally against `codex-cli 0.125.0` on 2026-04-27.

Verified in this repository:

- `codex plugin marketplace add <source>` exists.
- `codex plugin marketplace upgrade <marketplace-name>` exists.
- `codex plugin marketplace remove <marketplace-name>` exists.
- Codex accepts this repository as a local marketplace source.
- Git can clone `https://github.com/forsonny/deep-discovery.git`.
- Codex records marketplace registrations in `CODEX_HOME/config.toml`.
- Codex requires `.agents/plugins/marketplace.json` for repo marketplace discovery.
- Codex requires `.codex-plugin/plugin.json` for plugin metadata.
- Codex CLI does not expose a shell-level `codex plugin install` command.

Not verified in this session:

- the final install click path inside the Codex Plugins UI

Known Windows CLI caveat:

- In this Windows environment, `codex plugin marketplace add forsonny/deep-discovery`
  failed during Codex's Git staging clone. `git clone` followed by
  `codex plugin marketplace add .` succeeded.

## Install

Register the marketplace from GitHub:

```powershell
codex plugin marketplace add forsonny/deep-discovery
```

On Windows, if the remote marketplace command fails with a Git staging-path
error, clone the repository and register the local checkout:

```powershell
git clone https://github.com/forsonny/deep-discovery.git
cd deep-discovery
codex plugin marketplace add .
```

For an existing local checkout, run this from the repository root:

```powershell
codex plugin marketplace add .
```

Restart Codex, open Plugins, switch the filter from `Built by OpenAI` to a view
that includes third-party marketplaces, and install `deep-discovery` from
`Deep Discovery Plugins` / `deep-discovery-marketplace`.

To fetch marketplace updates later:

```powershell
codex plugin marketplace upgrade deep-discovery-marketplace
```

## Verify

After installing the plugin in the Codex UI, start a new Codex session and use an
explicit trigger:

```text
Run deep discovery on this architecture.
```

Expected behavior:

- The `deep-discovery` skill is visible as an installed skill.
- Codex loads `skills/deep-discovery/SKILL.md` when the prompt asks for deep
  discovery, 100-question brainstorming, architecture stress testing, strategy
  vetting, plugin or skill auditing, or similar planning review.

## Files

- `../.agents/plugins/marketplace.json` - Codex repo marketplace manifest
- `../.codex-plugin/plugin.json` - Codex plugin manifest
- `../skills/deep-discovery/SKILL.md` - main skill file
- `../skills/deep-discovery/references/` - domain-specific reference patterns
