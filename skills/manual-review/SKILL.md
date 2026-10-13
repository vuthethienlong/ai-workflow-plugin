---
name: manual-review
description: Resume a review interactively from prior findings and discuss evidence and remaining decisions without implying approval.
---

# Manual review

## Inputs
Target type and exact revision, prior checklist/findings, conversation/handover, current evidence.

## Steps
1. Read prior findings and handover first. If unavailable, state the missing context; do not invent outcomes.
2. For a PR, fetch its current state and head SHA before review. Reconcile discussion with evidence on the exact revision; update each finding status and record remaining decisions.
3. Re-review changed targets as a new revision using [review checklist](../../templates/review-checklist.md) and [findings](../../templates/review-findings.md).
4. Before changing PR status, fetch state and head SHA again. Follow the merged/stale/open decision in [review policy](../../references/review-policy.md); preserve checklist results and record `content_review`, `pr_gate`, and `next_action` independently from human approval.

## Artifacts
Updated checklist, findings, and handover if continuing later.

## Stop and handoff
Stop when evidence is missing or a human decision is required. Send actionable findings to owner. Human approval is separate; see [approval policy](../../references/approval-policy.md).

## Invocation
“Read \`ai-workflow/skills/manual-review/SKILL.md\` and review findings for PR [id] at commit [sha]. Continue review and explain blockers.”
