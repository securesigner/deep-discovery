# Codex Plugin / Skill Creation Pattern

Use this pattern when planning, auditing, repairing, or packaging a Codex plugin
or skill. Focus on whether future Codex runs will discover the right capability,
load only the right context, follow the intended workflow, and have clear
validation evidence after installation.

## Foundation (Q1-Q10)

- What is the goal, and how do we get there?
- Is this a plugin, a skill-only plugin, an MCP/app plugin, a marketplace bundle, or a local configuration change?
- Who should invoke it, and what exact user prompts should trigger it?
- What problem does it solve that existing Codex/system skills do not already solve?
- What artifacts are required: `.codex-plugin/plugin.json`, `skills/`, `references/`, `assets/`, `scripts/`, hooks, MCP servers, or apps?
- What should be invoked implicitly through metadata vs explicitly by name?
- What dependencies, network access, credentials, permissions, or external services are required?
- What must live in source, plugin cache, marketplace metadata, and user config?
- What validation evidence proves Codex loads and can use it?
- What is intentionally out of scope for this plugin or skill?

## Mechanics (Q11-Q30)

- Plugin manifest fields, folder name, and normalized plugin identity
- Marketplace entry path, policy, category, installation state, and product gating
- User config enablement and marketplace registration
- Source-to-cache sync or install workflow
- Skill frontmatter name, trigger description, and keyword coverage
- `.codex-plugin/plugin.json` interface display name, short description, brand color, and default prompts
- Progressive disclosure: what stays in `SKILL.md` vs reference files
- Reference file routing, one-level file layout, and when each file should be read
- Scripts, assets, hooks, MCP servers, apps, and whether each is actually needed
- Windows path handling, shell assumptions, and cross-platform command examples
- Versioning, update workflow, and stale cache behavior
- Conflict handling with existing skills, plugins, aliases, and user instructions
- Security boundaries for secrets, filesystem access, network access, and command execution
- Failure mode when the plugin is disabled, missing, malformed, or only partially installed
- What the user sees in Codex UI and what future Codex sees in skill metadata

## Stress Testing (Q31-Q50)

- What happens if `plugin.json` is invalid JSON or the folder name does not match the plugin name?
- What happens if the skill frontmatter is invalid YAML, overlong, vague, or uses the wrong name?
- What happens if the marketplace path points to the wrong root or stale source?
- What happens if the source plugin is updated but the cache copy is stale?
- What happens if Codex loads the plugin but not the intended skill?
- What happens if the trigger is too narrow and the skill is missed?
- What happens if the trigger is too broad and the skill loads in unrelated conversations?
- What happens if another skill has a similar name, similar description, or overlapping instructions?
- What happens if a reference file is not linked from `SKILL.md` or the routing index?
- What happens if `SKILL.md` becomes large enough to defeat progressive disclosure?
- What happens if a future agent follows old monolithic documentation instead of the split files?
- What happens if the plugin assumes a tool, app, MCP server, subagent, or browser capability that is unavailable?
- What happens if the plugin contains secrets, user-specific paths, or machine-specific state?
- What happens if installation succeeds but Codex must be restarted or cache refreshed before it is visible?
- What user-facing behavior would reveal the plugin is half-installed?

## Alternatives / Prior Art (Q51-Q65)

- Is a plugin required, or would a standalone skill be simpler?
- Is a new skill required, or should an existing skill be updated?
- Should this be project-local AGENTS instructions instead of a reusable skill?
- Should this be an MCP/app integration instead of process documentation?
- Should references be split by domain, provider, workflow phase, or artifact type?
- Can an existing scaffold script, validation script, or packaged example be reused?
- Which parts duplicate built-in Codex guidance and should be removed?
- Which parts need deterministic scripts instead of prose?
- What would a minimal plugin contain if all nice-to-have pieces were removed?
- What would make this easier to publish, install, or audit later?

## Feasibility (Q66-Q80)

- Can basic skill validation run with `quick_validate.py` on source and cache copies?
- Can `plugin.json` and `marketplace.json` parse as JSON?
- Can `codex debug prompt-input` show the skill metadata for realistic trigger prompts?
- Can the cache copy be synced without deleting unrelated user changes?
- Can the marketplace registration and plugin enablement be verified from user config?
- Can future maintainers understand which files are source of truth?
- Can updates be applied without requiring network access or private credentials?
- Can the plugin work when the workspace is not a git repository?
- Can the plugin work on Windows paths with spaces?
- Can the validation commands fail loudly when the plugin is not discoverable?

## Refinement (Q81-Q90)

- Which trigger words should be added or removed from the description?
- Which instructions can be moved out of `SKILL.md` into references?
- Which reference files are too small, too large, overlapping, or hard to route to?
- Which examples are concrete enough to guide future Codex runs?
- Which scripts or assets are unused and should be removed?
- Which validation commands belong in the plugin's maintenance notes vs the final response?
- Which installation or restart caveat should be made explicit?
- Which user-specific paths should be generalized or documented as local-only?
- Which names, categories, and UI labels need to be clearer?
- What is the smallest change that makes the plugin easier to use correctly?

## Synthesis (Q91-Q100)

- Final plugin or skill plan
- Final plugin or skill audit verdict
- Files to create, edit, split, or remove
- Trigger prompts that should and should not activate the skill
- Validation commands and expected evidence
- Installation, cache sync, and restart notes
- Top risks that remain after the changes
- Concrete follow-up work, if any
- Honest assessment of whether the plugin is ready to use with Codex
