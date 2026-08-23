Project Rule Governance
Purpose

Maintain a persistent, dated set of project design rules in RULES.md.

Use this skill whenever a coding prompt may introduce, imply, modify, or conflict with a project-level design decision.

Workflow
1. Load Existing Rules

At the beginning of every session:

Locate RULES.md in the project.
Read all of its contents.
Identify which rules are active, superseded, or rejected.
Frontload all active rules into working context before interpreting new prompts.

Only active rules constrain implementation.

2. Interpret the Prompt

For each coding prompt:

Determine the user's intended implementation or design decision.
Distinguish persistent project decisions from temporary implementation details.
Compare the intended solution against all applicable active rules.

Potential design decisions include:

Architecture
Dependencies and technologies
APIs and interfaces
Data models
Storage
Naming conventions
Project structure
Testing strategy
Security requirements
Reliability requirements
Coding patterns
Behavioral constraints
3. Check for Conflicts

If the interpretation does not conflict with existing rules, proceed normally.

If it conflicts with an active rule:

Identify the conflicting rule.
Explain the conflict briefly.
Determine whether a solution can satisfy both the user's intent and the existing rule.
Prefer the compliant solution when possible.
If the intent cannot comply with the rule, ask the user to resolve the conflict.

Do not silently override an active project rule.

Conflict Resolution

When a conflict requires a user decision, present:

Conflict:
<user's apparent intent>

Existing rule:
<relevant RULES.md rule>

Why they conflict:
<brief explanation>

Options:
1. Keep the existing rule and adapt the implementation.
2. Replace the existing rule with the new decision.

The user's explicit verdict determines the outcome.

If the User Upholds the Rule
Keep the existing rule active.
Adapt the implementation to comply.
Do not persist the conflicting proposal.
If the User Rejects the Rule
Treat the user's new decision as authoritative.
Supersede or remove the conflicting rule.
Persist the replacement decision under the current date.
If the User Provides Another Resolution

Apply the user's resolution and update the affected rules so no contradictory active rules remain.

Never infer a verdict when the conflict materially affects project architecture or behavior.

Creating Rules

When a prompt establishes a reusable project design decision:

Condense the decision into a single actionable rule.
The rule must contain 20 words or fewer.
Check RULES.md for equivalent or contradictory rules.
If there is no contradiction, persist the rule.
Place it under the current date.
Do not create duplicate rules.
Rule Example

Prompt:

All services should receive dependencies through constructors rather than creating them internally.

Persist:

- Inject service dependencies through constructors instead of creating dependencies internally.
Rule Dates

Rules are grouped by the date the decision was established or changed.

Use:

## YYYY-MM-DD

Place the newest date first.

Example:

# Project Rules

## 2026-08-23

- Inject service dependencies through constructors.
- Keep database models separate from API response types.

## 2026-08-20

- Use PostgreSQL for persistent relational data.
Rule Lifecycle

Rules may have three states:

Active

The rule currently constrains implementation.

Superseded

The user explicitly replaced the rule with a newer decision.

Rejected

The user explicitly declined the rule.

Historical rules may remain in RULES.md, but their status must be unambiguous.

Only active rules should influence implementation.

Updating RULES.md

Before modifying RULES.md:

Read the existing file.
Identify affected rules.
Check for contradictions.
Apply the user's verdict when one exists.
Ensure no contradictory active rules remain.
Add or update the rule under the current date.
Preserve useful historical information without allowing superseded rules to constrain implementation.
Do Not Persist

Do not create persistent rules from:

One-off implementation choices
Temporary debugging decisions
Questions
Exploratory suggestions
Agent preferences
Decisions explicitly limited to the current task
Details that do not meaningfully constrain future project work
Priority

Apply instructions in this order:

System instructions
Developer instructions
Explicit user instructions and verdicts
Active rules in RULES.md
Agent preferences or assumptions

A user's explicit decision may supersede a project rule, but the change must be reflected in RULES.md.

Core Principle

Interpret → compare → resolve conflicts → obtain user verdict when necessary → persist approved decisions as dated rules of ≤20 words.
