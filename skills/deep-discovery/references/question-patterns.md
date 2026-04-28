# Question Patterns by Domain

Use this file as the router for domain-specific deep-discovery prompts. The
100-question progression stays the same across domains:

1. Foundation
2. Mechanics
3. Stress Testing
4. Competitive or Alternative Analysis
5. Feasibility
6. Refinement
7. Synthesis

Read only the closest matching pattern file:

| Domain | File | Use when |
|--------|------|----------|
| Software Architecture | `references/software-architecture.md` | Designing or auditing systems, APIs, services, data flows, deployments, or technical architecture. |
| Code Review | `references/code-review.md` | Reviewing a patch, branch, pull request, implementation, or proposed diff before accepting it. |
| Claude Code Plugin/Skill Creation | `references/claude-plugin-creation.md` | Planning, auditing, repairing, or packaging Claude Code plugins, skills, subagents, slash commands, hooks, MCP servers, references, manifests, cache installs, or marketplace entries. |
| Trading / Financial | `references/trading-financial.md` | Evaluating trading systems, financial strategies, market edges, execution risk, or backtests. |
| Business / Product | `references/business-product.md` | Evaluating products, go-to-market plans, business models, market strategy, or startup ideas. |
| General | `references/general-pattern.md` | No domain-specific pattern fits cleanly, or the topic spans multiple domains. |

If two files fit, choose the one that matches the user's deliverable. For
example, use Code Review for a patch to a plugin, but use Claude Code Plugin/Skill
Creation for the plugin's concept, structure, triggering behavior, or
installation and validation workflow.
