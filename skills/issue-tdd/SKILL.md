---
name: issue-tdd
description: Implement one issue from a human-approved, revision-identifiable specification using TDD and real verification evidence.
---

# Issue TDD

## Inputs
Issue context; approved spec and revision; approval record; codebase; test/build tools; dependency readiness.

## Steps
1. Verify spec approval, exact revision, dependencies, criteria, tasks, and environment. If unverifiable, stop and return to [issue-to-spec](../issue-to-spec/SKILL.md).
2. Create a feature branch from current `main` before editing; follow the [repository change gate](../../references/workflow-rules.md#repository-change-gate). Map explicit test cases to acceptance criteria; choose applicable unit/integration/contract/E2E/regression/security checks and explain omissions.
3. RED: add tests and run them; capture command, exit status, and evidence of the intended failure.
4. GREEN: make the smallest complete implementation; run tests and capture actual evidence.
5. REFACTOR without behavior change; rerun affected tests.
6. Run applicable verification, lint, typecheck, build, security/permission checks. Unrun, skipped, and failed checks are not passes.
7. Prepare a Draft PR targeting `main`, referencing issue and approved spec revision. If PR tooling is unavailable, report the PR gate blocked and keep changes on the feature branch. Request independent [code review](../auto-review/SKILL.md) or [manual review](../manual-review/SKILL.md) on the exact PR head commit.
8. Fix actionable findings tests-first where relevant; rerun and re-review each new revision. Stop blocked if a blocker remains.
9. Perform final verification, obtain \`recommend_approve\`, then **stop for human approval**. Only after approval and authorization may worker-owned ADO MCP record PR, evidence, and approved status. Do not auto-merge/deploy or claim issue complete without evidence and authority.

## Artifacts
Code diff/PR, criteria-to-tests map, command results, review findings, final verification, approval record, optional ADO update.

## Stop conditions and handoff
Stop for unverifiable spec, blocked dependencies, failed/unrun required checks, unresolved findings, or before human approval. After approval, report the exact verified revision and evidence to the user; use the [task handover template](../../templates/task-handover.md) if another session must continue.

## Invocation
“Read \`ai-workflow/skills/issue-tdd/SKILL.md\`. Implement Issue #[id] from the approved spec with TDD and real test evidence; request review and await my final approval.”
