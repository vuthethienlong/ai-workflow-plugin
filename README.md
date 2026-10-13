# ai-workflow

Portable, approval-gated Markdown Skills for Codex and Claude Code, distributed as one skills-only plugin. Eight existing workflows are retained, with a ninth ADO/Orca smoke-test Skill. The plugin includes shared references, templates and a copyable Orca task prompt.

## Repository change gate

Changes follow **Feature Branch → Draft PR → Independent Review → Recommend Approve → Human Approval → Merge**. Never push directly to `main`, rewrite its history, or auto-merge. See the [repository change gate](references/workflow-rules.md#repository-change-gate).

## Skills

| Skill | Purpose |
|---|---|
| [idea-to-backlog](skills/idea-to-backlog/SKILL.md) | Turn an idea or ADO item into a reviewed, approval-gated backlog proposal. |
| [issue-to-spec](skills/issue-to-spec/SKILL.md) | Produce Implementation Ready Spec Kit-style artifacts and request review/approval. |
| [issue-tdd](skills/issue-tdd/SKILL.md) | Implement from an approved revision with TDD and evidence gates. |
| [auto-brainstorm](skills/auto-brainstorm/SKILL.md) | Explore and record options within the invoked session. |
| [manual-brainstorm](skills/manual-brainstorm/SKILL.md) | Resume an interactive brainstorm from saved artifacts. |
| [auto-review](skills/auto-review/SKILL.md) | Read-only review of a specific revision. |
| [manual-review](skills/manual-review/SKILL.md) | Continue review using prior findings and evidence. |
| [auto-implement](skills/auto-implement/SKILL.md) | Apply Issue TDD guidance in the current session. |
| [ado-orca-smoke-test](skills/ado-orca-smoke-test/SKILL.md) | Guide one authorized ADO write and a two-session Orca handover smoke test. |

## Install

See [provider install and runtime-check instructions](docs/install.md). Codex uses the portable root `plugin.json`; Claude Code uses `.claude-plugin/plugin.json`. Both discover the same `skills/` tree. Keep `references/` and `templates/` alongside the Skills so their relative links continue to resolve.

This is a skills-only package. It does not include an ADO client, MCP server, Orca scheduler or background job definition. Configure ADO MCP separately on each worker. The Markdown in [create-orca-job.md](prompts/create-orca-job.md) is a copyable request to Orca's existing Run/Task/Dispatch mechanism, not a native schedulable job definition. Record actual execution evidence in the [smoke report](templates/ado-orca-smoke-report.md).

## Boundaries

Human approvals remain separate from review recommendations. ADO credentials and permissions belong to the executing worker. Never store tokens in this repository. The smoke test may create at most one clearly labeled item in an explicitly authorized test project and leaves it open for inspection. See the [ADO MCP guidance](references/ado-mcp-guidelines.md), [workflow rules](references/workflow-rules.md), and [approval policy](references/approval-policy.md).
