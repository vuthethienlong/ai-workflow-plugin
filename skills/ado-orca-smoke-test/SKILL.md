---
name: ado-orca-smoke-test
description: Run one evidence-based Orca Run/Task/Dispatch handover test between two distinct Codex sessions, with one authorized idempotent ADO Issue write by Worker A and independent read-back by Worker B.
---

# ADO and Orca smoke test

Use this Skill only when the user requests the narrow two-worker smoke test. Read [ADO MCP guidelines](../../references/ado-mcp-guidelines.md), [handover guidelines](../../references/handover-guidelines.md), and the [smoke report template](../../templates/ado-orca-smoke-report.md). Follow the supplied job prompt; this Skill does not schedule or dispatch itself.

## Preconditions

1. Use Orca's existing Run, Task, dependency, and Dispatch commands documented by the installed runtime. These commands create orchestration records, not a background scheduler. Do not invent a YAML loader, MCP server, or cross-session memory.
2. Confirm two distinct Codex workers and sessions can be dispatched through Orca. Keep each worker's transcript/trace reference.
3. In Worker A's own configured ADO MCP, verify the exact organization and explicitly authorized test project, discover its supported Issue-like work item type, and confirm create/read permissions. If target or test authorization is ambiguous, stop before writing and request it.
4. Use a unique `TASK_ID` marker in title and description. Search before create; if it already exists, verify and reuse that exact item. If a create outcome is uncertain, search before any retry. Never create a second item.

## Worker A — create and hand off

1. Read this Skill and ADO guidance. Resolve the target and type using configured MCP results, not assumptions. Never expose credentials.
2. Search ADO for the exact unique marker. Stop on an ambiguous duplicate or missing permissions.
3. Create at most one clearly labeled `[AI-WORKFLOW SMOKE TEST]` Issue-like item in the verified test project, with the task marker and a harmless test description.
4. Read the item back. Record ID, URL, actual type, project, created timestamp if returned, tool result, worker/session identity, Orca task/dispatch IDs, trace/transcript, completed stage, and `NEXT_EXPECTED_STEP=worker_b_verify`.
5. Hand off through the existing Orca dependency/Run/Task/Dispatch mechanism. Do not put Worker A's item ID, summary, or next step in Worker B's prompt. Let Worker B recover them from Orca state.

## Worker B — recover and verify

1. Start in a genuinely distinct Codex session. Query Orca task, dispatch, worker, and run records to recover predecessor state, item reference, and next expected step. Record the actual trace and fallback. The coordinator must not paste Worker A's summary or ID.
2. If the item reference cannot be recovered natively, do not guess or use a coordinator-pasted fallback; report missing context and stop as PARTIAL/BLOCKED.
3. Independently read the same item using Worker B's own configured ADO MCP. Compare ID, title, and project; record read-back result and session identity. Do not edit, close, or delete the item.

## Report and outcomes

Complete [the smoke report](../../templates/ado-orca-smoke-report.md) with Run/Task/Dispatch identifiers, distinct worker/session IDs, per-session trace or explicit unavailability, ADO read-back evidence, recovered handover fields, fallbacks, and limitations. Use `PASS` only when both workers and all required reads/handover are evidenced. Use `PARTIAL`, `BLOCKED`, or `FAIL` honestly for missing MCP/type/permissions/target, duplicates, unavailable second session, transfer errors, or inaccessible trace. Never infer success from this Markdown or an earlier unrelated handover experiment.

Leave a created test item open for inspection. Never delete it or modify other items. No Spec Kit, TDD, code PR, merge, deploy, Orca source change, or scheduler implementation is part of this test.
