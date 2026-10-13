# Shared workflow rules

## Repository change gate

All future changes to the consuming repository, including Markdown, Skills, templates, and review-driven fixes, must follow:

**Feature Branch → PR → Independent Review → Recommend Approve → Human Approval → Merge**

1. Create a feature branch from current `main` before editing. Never commit or push changes directly to `main`, force-push it, or rewrite its history.
2. Commit actual changes and open a Draft PR targeting `main`. If PR tooling is unavailable, keep changes on the feature branch and report the blocked PR gate; do not bypass it. Do not manufacture an empty PR.
3. Have a reviewer independent of the author use [auto-review](../skills/auto-review/SKILL.md) on the exact PR head commit. Record the completed checklist, findings, evidence, and recommendation. Fix findings on the branch, verify, and request independent re-review of each changed revision.
4. Require `recommend_approve` with no unresolved blocking findings, then stop for explicit human approval of that exact PR head. Record the human actor, revision, and approval evidence separately from the review recommendation.
5. Merge only after both gates and explicit human merge authorization. Never auto-merge or interpret `recommend_approve` as human approval. Any new commit invalidates prior review and approval; repeat both gates.

### PR review and manually merged PRs

Before reviewing a PR and before changing its status, fetch its current state and head SHA. Review the fetched head. An `OPEN` PR may continue through the normal gate only when the reviewed SHA still matches its current head; otherwise stop with a stale PR gate and review the new head. A `MERGED` PR must never be approved, reopened, or marked Ready for Review. Preserve its completed checklist separately from PR approval status, and compare the reviewed commit with current `main`. If unmerged changes remain, recommend a follow-up PR containing only those changes; if none remain, record a post-merge verification report. Never rewrite `main` or create an empty PR. If state, SHA, or comparison cannot be verified, mark the gate blocked and do not change PR status.

Report separate fields: `content_review: passed | failed | unverified`, `pr_gate: eligible | stale | merged | blocked`, and `next_action: human_approval | create_followup_pr | post_merge_report`. For a merged PR, use `pr_gate: merged` regardless of its content review result; choose the next action from comparison with current `main`.

The initial 34-file package at `adf1a6b4adcc59c15a1f49e7d0badc6d6f311d08` was already on `main`. Review that baseline directly and preserve it and its history; submit subsequent corrections and their report through a feature PR. These Markdown instructions define policy; they do not configure GitHub branch protection.

## Session rules

- Keep Planning Ready, Implementation Ready, Spec Approved, and Implementation Verified distinct.
- Read existing decisions and handover artifacts before resuming. Never invent missing history.
- Identify the exact artifact revision under discussion. A changed revision invalidates prior review.
- Record facts, assumptions, decisions, unresolved questions, evidence, and next step separately.
- Stop at critical missing requirements, unverifiable approval, unavailable required access, or failed gates.
- A Skill is guidance for the active agent session. It does not schedule work, preserve state automatically, or activate another Skill by itself.
- Handoff explicitly to the next named workflow and identify its required inputs.
