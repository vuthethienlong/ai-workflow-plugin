# Independent review policy

Review the named target (spec or code, including Markdown instructions) at an exact commit/revision. For PR reviews, fetch the current PR state and head SHA before review and again before changing PR status. For repository changes, the reviewer must be independent of the author; if unavailable, report the review gate blocked. Do not mutate the target during review. Record checklist evidence and actionable findings with severity, location, impact, and resolution condition. Reviewer rechecks fixes on the new revision; author does not approve their own change.

Follow the [repository change gate](workflow-rules.md#repository-change-gate). Record independent outcomes: `content_review: passed | failed | unverified`, `pr_gate: eligible | stale | merged | blocked`, and `next_action: human_approval | create_followup_pr | post_merge_report`. Preserve completed checklist results when PR status changes; PR approval or merge status never replaces the content review result.

Apply this PR-state decision in order:

1. Fetch current PR state and head SHA. Review the identified commit, then fetch state and SHA again immediately before any PR status change.
2. If the PR is `OPEN` and the reviewed SHA equals its current head, use the normal review gate. Set `pr_gate: eligible` only after all required checks pass. Any head mismatch is `stale`; do not approve or mark Ready until the new head is reviewed.
3. If the PR is `MERGED`, never approve it, reopen it, or mark it Ready for Review. Keep the checklist and `content_review` result. Compare the reviewed commit with current `main` and identify changes that remain unmerged.
4. If changes remain, set `next_action: create_followup_pr` and recommend a new PR containing only those changes. Never rewrite `main` or create an empty PR. If no changes remain, set `next_action: post_merge_report` and record a post-merge verification report with comparison evidence.
5. For unavailable or ambiguous PR state, inaccessible head SHA, or an incomplete comparison, set `pr_gate: blocked`; set `content_review: unverified` where review evidence is insufficient. Do not change PR status.

`recommend_approve` allows requesting human approval only for an open PR whose current head matches the reviewed SHA; it never authorizes merging automatically.

Recommendation values: `recommend_approve`, `changes_required`, `blocked`. This is separate from human approval. See [approval-policy.md](approval-policy.md), [review-checklist.md](../templates/review-checklist.md), and [review-findings.md](../templates/review-findings.md).
