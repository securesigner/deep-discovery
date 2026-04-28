# Claude Code Plugin / Skill Creation Pattern

Use this pattern when planning, auditing, repairing, or packaging a Claude Code
plugin, skill, subagent, slash command, hook, or MCP server. Focus on whether
future Claude Code sessions will discover the right capability, load only the
right context, follow the intended workflow, and have clear validation evidence
after installation.

## Foundation (Q1-Q10)

- What is the goal, and how do we get there?
- Is this a plugin, a skill-only drop-in (`~/.claude/skills/<name>/`), a subagent (`.claude/agents/*.md`), a slash command (`.claude/commands/*.md`), a hook (`settings.json`), an MCP server (`.mcp.json`), a marketplace bundle, or a project-local configuration change?
- Who should invoke it, and what exact user prompts or `/<command>` invocations should trigger it?
- What problem does it solve that existing built-in capabilities or already-installed plugins do not already solve?
- What artifacts are required: `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`, `skills/`, `commands/`, `agents/`, `hooks/`, `references/`, `assets/`, `scripts/`, MCP servers, settings hooks, or output styles?
- What should be invoked implicitly through skill metadata (description-driven routing) vs explicitly by name (slash commands, named subagents)?
- What dependencies, network access, credentials, permissions (`settings.json` `permissions` block), or external services are required?
- What must live in source, plugin cache (`~/.claude/plugins/`), marketplace metadata, user settings (`~/.claude/settings.json`), and project settings (`.claude/settings.json` / `settings.local.json`)?
- What validation evidence proves Claude Code loads and can use it?
- What is intentionally out of scope for this plugin, skill, subagent, or command?

## Mechanics (Q11-Q30)

- Plugin manifest fields, folder name, and normalized plugin identity
- Marketplace entry path, source format (relative path, `github`, `url`, `git-subdir`, `npm`), policy, category, and tags
- User config enablement and marketplace registration via `/plugin marketplace add` and `/plugin install <plugin>@<marketplace>`
- Source-to-cache sync, plugin update flow, and behavior of `/plugin marketplace update`
- Skill frontmatter `name` (kebab-case, must match folder), `description` (trigger phrases), and keyword coverage
- `.claude-plugin/plugin.json` `description`, `version`, `author`, `homepage`, `repository`, `license`, `keywords`
- Component auto-discovery vs explicit paths in `plugin.json` (`skills`, `commands`, `agents`, `hooks`, `mcpServers`, `outputStyles`)
- Progressive disclosure: what stays in `SKILL.md` vs reference files loaded on demand
- Reference file routing, one-level file layout, and when each file should be read
- Subagent definition: YAML frontmatter (`name`, `description`, optional `tools`, `model`), system prompt body, and isolation semantics
- Slash command file format and argument handling (`$1`, `$ARGUMENTS`)
- Hook events (`SessionStart`, `UserPromptSubmit`, `PreToolUse`, `PostToolUse`, `Stop`, etc.), matchers, and command/script payloads
- MCP server configuration, transport (stdio/http/sse), and per-tool permission rules
- Permissions model: `allow`/`deny`/`ask` lists, tool-specific patterns (`Bash(git diff:*)`)
- Cross-platform path handling, shell assumptions, and Windows/Unix command examples
- Versioning, update workflow, and stale cache behavior
- Conflict handling with existing skills, plugins, subagents, slash commands, aliases, and user instructions
- Security boundaries for secrets, filesystem access, network access, and command execution
- Failure mode when the plugin is disabled, missing, malformed, or only partially installed
- What the user sees in `/plugins` UI and what future Claude Code sees in skill metadata

## Stress Testing (Q31-Q50)

- What happens if `.claude-plugin/plugin.json` is invalid JSON or the folder name does not match the plugin name?
- What happens if `.claude-plugin/marketplace.json` is missing `name`, `owner.name`, or `plugins`?
- What happens if the skill frontmatter is invalid YAML, overlong, vague, or uses the wrong name?
- What happens if a plugin source path in `marketplace.json` is wrong, dangling, or points at stale revision?
- What happens if the source plugin is updated but the cache copy is stale (no `/plugin marketplace update` run)?
- What happens if Claude Code loads the plugin but not the intended skill, subagent, or command?
- What happens if the skill description trigger is too narrow and the skill is missed?
- What happens if the trigger is too broad and the skill loads in unrelated conversations?
- What happens if another skill or subagent has a similar name, similar description, or overlapping instructions?
- What happens if a reference file is not linked from `SKILL.md` or the routing index?
- What happens if `SKILL.md` becomes large enough to defeat progressive disclosure?
- What happens if a hook fires during an unexpected event and blocks routine work?
- What happens if a hook script fails, hangs, or has a non-zero exit code?
- What happens if an MCP server is unavailable, slow, or returns malformed responses?
- What happens if the plugin assumes a tool, MCP server, subagent, or model capability that is unavailable in the user's environment?
- What happens if the plugin contains secrets, user-specific paths, or machine-specific state?
- What happens if installation succeeds but Claude Code must be restarted before the plugin is visible?
- What happens if `permissions` rules in `settings.json` block the tool calls the skill needs?
- What user-facing behavior would reveal the plugin is half-installed?

## Alternatives / Prior Art (Q51-Q65)

- Is a plugin required, or would a standalone skill drop-in (`~/.claude/skills/<name>/`) be simpler?
- Is a new skill required, or should an existing skill be updated?
- Should this be a project-local `CLAUDE.md` instruction instead of a reusable skill?
- Should this be a slash command instead of a skill (explicit invocation vs implicit triggering)?
- Should this be a subagent instead of a skill (isolated context vs in-conversation)?
- Should this be a hook instead of an instruction (deterministic automation vs prompted behavior)?
- Should this be an MCP server instead of process documentation?
- Should references be split by domain, provider, workflow phase, or artifact type?
- Can an existing scaffold script, validation script, or packaged example be reused?
- Which parts duplicate built-in Claude Code guidance and should be removed?
- Which parts need deterministic scripts or hooks instead of prose?
- What would a minimal plugin contain if all nice-to-have pieces were removed?
- What would make this easier to publish, install, or audit later?

## Feasibility (Q66-Q80)

- Can `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` parse as JSON?
- Can the skill be exercised end-to-end with a realistic trigger prompt in a fresh session?
- Can the marketplace registration and plugin enablement be verified from `/plugins` and user config?
- Can the cache copy be synced via `/plugin marketplace update` without deleting unrelated user changes?
- Can future maintainers understand which files are source of truth?
- Can updates be applied without requiring network access or private credentials?
- Can the plugin work when the workspace is not a git repository?
- Can the plugin work on Windows paths with spaces and on macOS/Linux without modification?
- Can validation commands fail loudly when the plugin is not discoverable?
- Can hooks be tested in isolation before being shipped?
- Can MCP servers start cleanly and be reachable from the Claude Code process?
- Can subagents be invoked from the parent skill without circular triggering?

## Refinement (Q81-Q90)

- Which trigger words should be added or removed from the skill description?
- Which instructions can be moved out of `SKILL.md` into references?
- Which reference files are too small, too large, overlapping, or hard to route to?
- Which examples are concrete enough to guide future Claude Code runs?
- Which scripts, hooks, or assets are unused and should be removed?
- Which validation commands belong in the plugin's maintenance notes vs the final response?
- Which installation or restart caveat should be made explicit?
- Which user-specific paths should be generalized or documented as local-only?
- Which names, categories, tags, and UI labels need to be clearer?
- What is the smallest change that makes the plugin easier to use correctly?

## Synthesis (Q91-Q100)

- Final plugin or skill plan
- Final plugin or skill audit verdict
- Files to create, edit, split, or remove
- Trigger prompts (or slash commands) that should and should not activate the skill
- Validation commands and expected evidence
- Installation, cache sync, and restart notes
- Top risks that remain after the changes
- Concrete follow-up work, if any
- Honest assessment of whether the plugin is ready to use with Claude Code
