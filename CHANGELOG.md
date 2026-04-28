# Changelog

## [1.1.0] - 2026-04-28

- Adapted plugin packaging from Codex CLI to Claude Code.
- Replaced `.codex-plugin/plugin.json` with `.claude-plugin/plugin.json`.
- Replaced `.agents/plugins/marketplace.json` with `.claude-plugin/marketplace.json`.
- Renamed and rewrote `references/codex-plugin-creation.md` as `references/claude-plugin-creation.md`, covering Claude Code plugins, skills, subagents, slash commands, hooks, and MCP servers.
- Updated `SKILL.md` and `references/question-patterns.md` to reference Claude Code conventions and the Agent tool for delegation.
- Replaced `docs/README.codex.md` with `docs/README.claude.md` and rewrote `README.md` install instructions for `/plugin marketplace add` and the `~/.claude/skills/` drop-in path.
- Removed Codex-specific install caveats, validation scripts, and marketplace files.

## [1.0.0] - 2026-04-27

- Published the initial Codex plugin manifest for `deep-discovery`.
- Added the Codex repo marketplace manifest.
- Added the `deep-discovery` skill and domain reference patterns.
- Added Codex install, usage, validation, and license documentation.
- Documented the verified Windows clone-and-register fallback.
