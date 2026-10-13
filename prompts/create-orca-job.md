# Create an Orca ADO smoke-test task

Replace every angle-bracket value with verified values before using this prompt. Keep `TASK_ID` unique. This is a copyable natural-language request for Orca's existing Run/Task/Dispatch mechanism, not an Orca-native schedulable job definition.

```text
TASK_ID: <unique task ID>
ADO_ORGANIZATION: <verified authorized organization>
ADO_PROJECT: <verified authorized test project>
TEST_WORK_ITEM_TYPE: <actual supported Issue-like type discovered by Worker A>
WORKER_A: <Codex worker A>
WORKER_B: <distinct Codex worker B>
SOURCE_SKILL: skills/ado-orca-smoke-test/SKILL.md

Create and dispatch exactly one short test task using Orca's existing Run/Task/dependency/Dispatch mechanism. Read SOURCE_SKILL and follow it. Do not invent a job loader, scheduler, MCP server, or cross-session memory.

Worker A (Session A):
- Read SOURCE_SKILL and references/ado-mcp-guidelines.md.
- Using Worker A's configured ADO MCP, verify the organization, explicitly authorized test project, discovered work-item type, and write/read permissions. Stop before any write if any is missing or ambiguous.
- Search for TASK_ID marker first. Create at most one item titled `[AI-WORKFLOW SMOKE TEST] <TASK_ID>` using the discovered type; if an exact marker already exists, safely reuse and verify it. If create outcome is uncertain, search before any retry.
- Read the item back; record ID, URL, type, project, timestamp if returned, tool result, worker/session identity, Orca Run/Task/Dispatch IDs and readable trace.
- Record completed stage and NEXT_EXPECTED_STEP=worker_b_verify in Orca task state/result.
- Hand off through Orca's native existing dependency/dispatch mechanism. Dispatch Worker B with only the task reference and instruction to recover the predecessor context from Orca. Never paste Worker A's summary, item ID, URL, or next action in Worker B's prompt.

Worker B (Session B):
- Run as a genuinely distinct Codex worker in a distinct session.
- Independently inspect Orca Run/Task/Dispatch/worker records to recover Worker A's result, ADO reference, and NEXT_EXPECTED_STEP. Record what crossed the handover and the trace. Do not accept coordinator-pasted context as native recovery.
- Using Worker B's own configured ADO MCP, independently read the recovered item and compare ID, title/marker, and project. Do not create, edit, close, or delete an item.
- Report PASS only if native handover and independent ADO read-back are evidenced; otherwise report PARTIAL, BLOCKED, or FAIL with the exact missing evidence.

Allowed actions: read the named package files; inspect Orca task/trace state; ADO search/read; at most one authorized, idempotent test Issue-like create by Worker A; Orca handoff and reporting.
Stop conditions: no ADO MCP; unverified organization/project/test authorization; unsupported type; missing permissions; ambiguous/existing duplicate; uncertain write without resolved search; no distinct Worker B session; failed transfer; missing required evidence. Do not retry writes blindly. Leave any created item open for user inspection.

Final report fields: TASK_ID; STATUS (PASS/PARTIAL/BLOCKED/FAIL); ADO organization/project/type/ID/URL/read-back; Orca Run/Task/Dispatch IDs; Worker A/B identities and distinct session IDs; trace/transcript reference for each; recovered context and NEXT_EXPECTED_STEP; automatic handover result; fallback used; missing evidence; blocker and next step.

Out of scope: full Idea→Spec→TDD→Review→Merge flow, Spec Kit, code PR, merge, deploy, Orca source changes, new scheduler, cleanup of the test item, or claims of success without tool/trace evidence.
```
