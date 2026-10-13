---
name: auto-review
description: Independently review a spec or code revision without mutation and return evidence, findings, and a recommendation.
---

# Auto review

## Inputs
Target type, exact artifact revision/commit, acceptance criteria, relevant test evidence, prior findings if re-reviewing.

## Steps
1. For a PR, fetch its current state and head SHA; confirm the target revision. Read prior findings on re-review. Do not edit target.
2. Evaluate [review checklist](../../templates/review-checklist.md), correctness, scope, errors, security/privacy, compatibility, and evidence.
3. Save checklist and [findings](../../templates/review-findings.md); mark each finding resolved only with evidence on this revision.
4. For a PR, fetch state and head SHA again before any status change. Apply the merged/stale/open decision and record separate `content_review`, `pr_gate`, and `next_action` outcomes from [review policy](../../references/review-policy.md). Keep checklist results separate from PR approval status.
5. Recommend \`recommend_approve\`, \`changes_required\`, or \`blocked\`; keep \`review_status\` separate from human \`approval_status\`.

## Artifacts
Completed review checklist and findings for exact revision.

## Stop and handoff
Stop if the revision or necessary evidence is unavailable; report blocked. Send findings to owner for fixes and re-review. Recommendation never constitutes approval; see [review policy](../../references/review-policy.md).

## Invocation
“Read \`ai-workflow/skills/auto-review/SKILL.md\`. Review [target] at [revision] without editing it and provide evidence and findings.”
