---
name: issue-to-spec
description: Expand one issue into Implementation Ready Spec Kit-style Markdown and request independent review and human approval.
---

# Issue to spec

## Inputs
Issue ID/description; approved planning artifacts; prior handover; repository context; available Git/PR and worker-owned ADO MCP access.

## Steps
1. Read issue, decisions, approval records, handover, and relevant actual code. Record conflicts and missing context. ADO reads follow [ADO MCP guidelines](../../references/ado-mcp-guidelines.md).
2. Use [Auto Brainstorm](../auto-brainstorm/SKILL.md) or [Manual Brainstorm](../manual-brainstorm/SKILL.md). Explore options, trade-offs, interfaces, security, data, failures, migration, and simplicity.
3. Before repository edits, create a feature branch from current `main` under the [repository change gate](../../references/workflow-rules.md#repository-change-gate). Create [spec](../../templates/speckit/spec.md), [plan](../../templates/speckit/plan.md), [tasks](../../templates/speckit/tasks.md), and [requirements checklist](../../templates/speckit/requirements-checklist.md). Add research/data/contracts only when needed. Do not claim Spec Kit CLI use unless actually run.
4. Cross-check criteria ↔ tasks ↔ plan and ensure tests cover every criterion. Record unresolved questions; do not certify Implementation Ready with blockers.
5. For repository edits, prepare a documentation-only Draft PR targeting `main`. If Git/PR tooling is unavailable, report the PR gate blocked and preserve reviewable artifacts without writing to `main`. A PR is not a merge.
6. Request an independent, read-only [review](../auto-review/SKILL.md) or [manual review](../manual-review/SKILL.md) against exact revision. Fix findings and re-review the updated revision.
7. Present review recommendation and exact artifact revision. **Stop for explicit human spec approval.** Record it using [approval record](../../templates/approval-record.md).
8. Only after approval, optionally update ADO with worker-owned MCP reference, revision, and state. Never mark implemented.

## Artifacts
Spec, plan, tasks, checklist, review findings/checklist, approval record, optional documentation PR and ADO reference.

## Stop conditions and handoff
Stop on unverifiable input/approval, unresolved blocker, missing critical requirement, or before human approval. Handoff approved revision and exact criteria to [issue-tdd](../issue-tdd/SKILL.md).

## Invocation
“Read \`ai-workflow/skills/issue-to-spec/SKILL.md\`. Expand ADO Issue #[id] into a detailed Spec Kit-style spec and request an independent review. Stop for my spec approval.”
