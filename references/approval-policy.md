# Approval policy

Keep these fields distinct: `review_status`, `review_recommendation`, `approval_status`, `approval_actor`, `artifact_revision`.

Defaults: `approval_status: pending_human_approval`; `auto_approve_enabled: false`. Review is an evidence-based recommendation, never a human approval event. Only the human may approve a specified artifact revision. Artifact changes make approval/review stale. No auto-approval is enabled or implemented.

External writes, including ADO changes, require explicit approval of the exact proposed action and configured, authorized worker tooling.

For repository changes, follow the [repository change gate](workflow-rules.md#repository-change-gate). Explicit instructions to create a branch, push it, or open a Draft PR authorize those actions only; they are not human approval to merge. Record the PR URL, exact head commit, human actor, and approval evidence. Never enable auto-merge. A human merge authorization is required after independent `recommend_approve` and human approval of the current revision.
