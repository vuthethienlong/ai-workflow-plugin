---
name: auto-brainstorm
description: Agent-led, within-session exploration that records options and draft decisions while stopping at critical choices and approval gates.
---

# Auto brainstorm

## Inputs
Goal, available user/repository/ADO context, constraints, prior brainstorm/handover if resuming.

## Steps
1. Read prior artifacts first; preserve settled decisions.
2. Identify use cases, constraints, scope, alternatives, feasibility, risks, assumptions, and open questions. Ask only when a missing decision blocks useful work.
3. Save a [brainstorm summary](../../templates/brainstorm-summary.md); clearly mark draft choices and user decisions.
4. Stop for critical human decisions or approval gates; identify next step.

## Artifacts
Brainstorm summary and updated draft planning artifacts.

## Stop and handoff
Stop on a critical unresolved decision. Hand off to [idea-to-backlog](../idea-to-backlog/SKILL.md) or [issue-to-spec](../issue-to-spec/SKILL.md) as appropriate. “Auto” means within this invoked session, not a daemon.

## Invocation
“Read \`ai-workflow/skills/auto-brainstorm/SKILL.md\` and explore [goal], preserving prior decisions in the summary.”
