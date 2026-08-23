AGENTS.md
Purpose

This agent maintains a concise, persistent set of project rules derived from explicit design decisions in user prompts.

Session Initialization

At the start of every session:

Read RULES.md if it exists.
Frontload all rules from every date category in RULES.md into the agent's working context before processing the user's request.
Treat those rules as project constraints unless they conflict with a higher-priority instruction or a newer explicit user decision.
Do not silently discard, rewrite, or weaken existing rules.
Detecting Design Decisions

For every user prompt, evaluate whether it contains a design decision relevant to the coding project.

A design decision includes, but is not limited to:

Architecture or system structure
Technology or dependency choices
API or interface conventions
Data models or storage decisions
Naming or organizational conventions
Testing requirements
Security or reliability requirements
Coding patterns or implementation constraints
Explicit decisions about how the project should behave

Do not persist ordinary requests, temporary implementation details, questions, or preferences that are not intended to establish a reusable project rule.

Rule Condensation

When a prompt contains a persistent design decision, condense each decision into one rule of no more than 20 words.

The condensed rule must:

Preserve the essential intent of the decision.
Be specific enough to guide future implementation.
Avoid unnecessary explanation or rationale.
Be phrased as an actionable project rule.
Persistence and Date Categorization

Before adding a new rule:

Read the current RULES.md.
Check whether an existing rule already expresses the decision.
Check for contradictions with existing rules.
If the new rule contradicts an existing rule, do not persist it automatically. Follow the existing rule unless the user explicitly resolves the conflict.
If there is no contradiction, append the condensed rule under the current date.
Create a date heading in RULES.md if one does not already exist for the current date.
Use the format ## YYYY-MM-DD.
Keep rules grouped chronologically, with the newest date first.
Create RULES.md if it does not exist.
Keep RULES.md limited to persistent project rules.
Rule Format

Each rule must be a Markdown bullet under its date heading.

Example:

# Project Rules

## 2026-08-23

- Use dependency injection for services that require external infrastructure.
- Keep API response types separate from database models.

## 2026-08-20

- Prefer PostgreSQL for persistent relational project data.

Each rule must contain 20 words or fewer. The date heading does not count toward the rule's word limit.

Updating Existing Rules

When a user explicitly changes an existing design decision:

Identify the affected existing rule.
Treat the new decision as authoritative.
Do not leave contradictory rules active.
Replace or amend the old rule as appropriate.
Record the updated decision under the current date.
Preserve historical date sections when useful, but ensure the active rules are unambiguous.
Priority

Explicit user instructions in the current prompt take precedence over persisted rules when they intentionally change or supersede an existing design decision.

Higher-priority system or developer instructions always take precedence over RULES.md.

Operational Principle

Evaluate every prompt for design decisions; persist reusable decisions as ≤20-word rules under the current date when no contradiction exists.
