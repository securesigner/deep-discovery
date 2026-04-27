# Software Architecture Pattern

Use this pattern when stress-testing a system design, service architecture, API,
data model, infrastructure plan, or technical migration.

## Foundation (Q1-Q10)

- What is the goal, and how do we get there?
- What problem does this solve that is not already solved?
- Who are the users and what are their actual workflows?
- What are the hard constraints (budget, timeline, team size, tech stack)?
- What are the non-negotiable requirements vs nice-to-haves?
- What does success look like in 1 month? 6 months? 1 year?
- What is the simplest version that would be useful?
- What existing systems does this interact with?
- What data flows through this system?
- What are the trust boundaries?

## Mechanics (Q11-Q30)

- Component responsibilities and boundaries
- Data storage and retrieval patterns
- API contracts between components
- Authentication and authorization model
- Error handling and recovery
- Deployment and infrastructure
- Monitoring and observability
- State management
- Concurrency and race conditions
- Configuration and environment management

## Stress Testing (Q31-Q50)

- What happens when component X fails?
- What is the blast radius of a specific failure?
- How does this behave under 10x load? 100x?
- What are the single points of failure?
- What happens during partial network partitions?
- What does the worst-case latency look like?
- What happens when disk fills up?
- How does this handle clock skew?
- What happens when a dependency changes its API?
- What data can be lost and what is the recovery path?

## Competitive / Alternative Analysis (Q51-Q65)

- What existing solutions address this problem?
- Why not use the obvious alternative?
- What would a team 10x our size build differently?
- What would a team with no budget build?
- What patterns from other domains apply here?
- What open-source tools cover part of this?

## Feasibility (Q66-Q80)

- Can the team actually build this?
- What skills are missing?
- What is the riskiest technical component?
- What should be prototyped first?
- What third-party dependencies could block us?
- What is the migration path from current state?

## Refinement (Q81-Q90)

- What can be simplified?
- What is over-engineered for the current stage?
- What implicit assumptions are baked in?
- What would break if we scaled 100x?
- What operational burden does this create?

## Synthesis (Q91-Q100)

- What is the revised architecture?
- What are the top 3 risks?
- What is the build order?
- What is the honest assessment?
