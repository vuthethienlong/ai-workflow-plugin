# ai-workflow

Portable, approval-gated Markdown Skills for Codex and Claude Code, distributed as one skills-only plugin. Eight existing workflows are retained, with a ninth ADO/Orca smoke-test Skill. The plugin includes shared references, templates and a copyable Orca task prompt.

## Quick start

Install from the **public** repository `vuthethienlong/ai-workflow-plugin`. This package provides Markdown Skills only; it does not install Azure DevOps MCP or an Orca scheduler.

### Claude Code

```bash
claude plugin marketplace add vuthethienlong/ai-workflow-plugin
claude plugin install ai-workflow@ai-workflow
```

Start a **new Claude Code session**, then ask the agent to use a Skill (examples below). If the marketplace was already added before `.claude-plugin/marketplace.json` was published, refresh it:

```bash
claude plugin marketplace update ai-workflow
claude plugin marketplace list
```

As an alternative, clone this public repository and test the plugin without installing a marketplace:

```bash
git clone https://github.com/vuthethienlong/ai-workflow-plugin.git
claude --plugin-dir ./ai-workflow-plugin
```

### Codex

Codex plugin marketplace support depends on the installed CLI version. Clone the public repository for a local marketplace source, then inspect availability:

```bash
git clone https://github.com/vuthethienlong/ai-workflow-plugin.git
codex plugin marketplace add ./ai-workflow-plugin
codex plugin list --marketplace ai-workflow --available
```

If `ai-workflow` is listed, install it via the Codex plugin UI or your CLI's supported install command. The Codex catalog is `.agents/plugins/marketplace.json`; the portable manifest is `plugin.json`. These commands are examples to verify on the installed runtime, **not a claim of completed runtime testing**.

### Use the Skills

Ask the running Codex/Claude agent in natural language. The exact invocation syntax may differ between agent versions.

**1. Idea → Backlog** — brainstorm and propose Azure DevOps work items without creating them before approval:

```text
Use the ai-workflow idea-to-backlog Skill.
Brainstorm a Google sign-in feature and prepare an Epic/Issues/Tasks
proposal with dependencies and acceptance criteria.
Stop for my approval before writing anything to Azure DevOps.
```

**2. Issue → Spec** — produce planning artifacts for an existing issue:

```text
Use the ai-workflow issue-to-spec Skill.
Read ADO Issue #1234 using my authorized MCP.
Create spec.md, plan.md and tasks.md, open a Draft PR,
request independent review, and stop for human approval.
```

**3. Issue → TDD** — implement an approved specification:

```text
Use the ai-workflow issue-tdd Skill.
Implement the human-approved spec for Issue #1234 using
RED → GREEN → REFACTOR, run tests, create a Draft PR,
request independent review, and do not auto-merge.
```

**4. Brainstorm / review** — use the auxiliary Skills:

```text
Use ai-workflow auto-brainstorm to explore my feature proposal.
Use ai-workflow auto-review to review PR #15 at its current HEAD SHA.
Record findings and recommendations, but never approve or merge automatically.
```

**5. Orca + ADO smoke test** — requires existing Orca Run/Task/Dispatch and two separate configured workers:

```text
Use ai-workflow ado-orca-smoke-test for a single approved ADO
test work item and native handover between two separate Orca workers.
Collect real tool and session evidence. Do not create duplicates.
```

Additional Skills: `manual-brainstorm` resumes an interactive brainstorm, `manual-review` continues an evidence-based review, and `auto-implement` follows approved issue-to-TDD guidance inside the active session.

### Prerequisites and troubleshooting

- **Claude marketplace file not found:** verify [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) exists on the branch used by the CLI, update the marketplace, then retry.
- **Plugin not found:** check `claude plugin marketplace list` and that the plugin name is `ai-workflow` in marketplace `ai-workflow`.
- **Skill not discovered:** restart the agent session and check the plugin is enabled. Keep `skills/`, `references/`, and `templates/` together.
- **ADO MCP unavailable:** configure it separately in the executing worker with authorized credentials. Skills cannot provide MCP authentication.
- **Review and approval:** an independent reviewer can recommend approval; an authorized human must approve external writes and merges.
- **Runtime status:** manifest/link checks alone do **not** verify an installation in a clean Codex or Claude Code session.

For more installation details, see [docs/install.md](docs/install.md).

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
