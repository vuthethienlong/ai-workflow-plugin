---
name: idea-to-backlog
description: Turn a user idea or existing ADO work item into a reviewed, approval-gated backlog proposal.
---

# Idea to backlog

## Inputs
Idea or ADO work-item ID/URL; repository/project context if available; desired scope; Auto or Manual Brainstorm preference; publication mode.

## Steps
1. Clarify goal, users, boundaries, and desired outcome. Inspect existing planning and handover artifacts. For ADO context follow [ADO MCP guidelines](../../references/ado-mcp-guidelines.md); if MCP is absent, label reads and duplicate checks unavailable.
2. Apply [Auto Brainstorm](../auto-brainstorm/SKILL.md) or [Manual Brainstorm](../manual-brainstorm/SKILL.md). Nested activation is not guaranteed; read and follow its file if needed.
3. Draft planning-level requirements, scope/non-scope, acceptance criteria, decisions, assumptions, risks, and open questions. Label this Planning Ready, not Implementation Ready.
4. Decompose into only work-item types supported by the target project. Verify its hierarchy; never assume an Issue type. Make implementation candidates independently specifiable. Record dependencies, blocked edges, and possible parallel groups without claiming workers launched. Check duplicates when ADO reads are available; flag uncertain matches.
5. Produce complete editable [backlog proposal](../../templates/backlog-proposal.md) and [brainstorm summary](../../templates/brainstorm-summary.md). Include one publication mode: new Epic + approved children; Epic only; children under existing Epic; standalone items; planning-only.
6. **Stop for explicit human approval before any ADO write.** The approval must identify exactly which items and content are approved. Afterward, if authorized MCP exists, write only approved items, parent first as needed, avoid duplicate retries, verify IDs/URLs/links, report partial failures. Save approval record and outcomes.

## Artifacts
Brainstorm summary, backlog proposal, decision/approval record, dependency breakdown, optional verified ADO IDs/URLs.

## Stop conditions and handoff
Stop on critical ambiguity, unverifiable hierarchy, missing required permission, or before unapproved writes. Handoff Backlog Ready items to [issue-to-spec](../issue-to-spec/SKILL.md), one implementation item at a time.

## Invocation
“Read \`ai-workflow/skills/idea-to-backlog/SKILL.md\`. Brainstorm [idea] and prepare an Epic/Issue/Task proposal. Do not write to ADO until I explicitly approve.”
