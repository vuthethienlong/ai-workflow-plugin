---
name: auto-implement
description: In the active session, implement from an approved spec with TDD, evidence, and review gates; never schedule or approve autonomously.
---

# Auto implement

## Inputs
Human-approved spec and exact revision, issue, repository, dependencies, test tools, prior handover.

## Steps
1. Read [Issue TDD](../issue-tdd/SKILL.md), approval record, and handover. Verify inputs; otherwise stop and return to spec workflow.
2. Follow Issue TDD steps: criteria mapping, RED/GREEN/REFACTOR, actual verification, independent review on exact revision, finding loop.
3. Record evidence and approval status separately. Do not silently create external writes; after explicit approval, use only authorized worker-owned tools.

## Artifacts
Same as [issue-tdd](../issue-tdd/SKILL.md), plus task handover as needed.

## Stop and handoff
Stop at blocker, failed required check, unresolved review, or human approval gate. “Auto” is limited to work in this invoked session, not scheduling, cross-session memory, or automatic approval.

## Invocation
“Read \`ai-workflow/skills/auto-implement/SKILL.md\` and implement approved spec [path/revision] following TDD. Stop for review and human approval.”
