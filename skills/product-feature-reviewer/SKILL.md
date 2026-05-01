---
name: product-feature-reviewer
description: Review and critique product-level OpenSpec changes before implementation, checking analysis quality, hidden assumptions, repo impact, acceptance criteria, rollout, and risks.
---

# Product Feature Reviewer

Use this skill before creating repo implementation slices or before approving a product-level OpenSpec change.

## Review stance

Be skeptical but constructive. The goal is to catch ambiguity before it becomes cross-repo rework.

## Checklist

### Problem framing

- Is the problem clear without reading the proposed solution?
- Are users/actors identified?
- Is the current behavior documented?
- Is the desired outcome measurable?

### Scope

- Are goals and non-goals explicit?
- Are edge cases and error states covered?
- Are open questions separated from assumptions?

### Cross-repo impact

- Does `repo-impact.md` mention all expected repos?
- Are protobuf/API contract changes identified?
- Is implementation order plausible?
- Are backward compatibility and rollout addressed?

### Requirements

- Are requirements written as observable behavior?
- Are scenarios concrete enough for tests?
- Do local repo slices have enough context to begin?

### Risk

- Security / permissions?
- Data migration?
- Observability?
- Kill switch / rollback?
- Partial rollout and mixed-version compatibility?

## Output format

Return:

```md
# Review

## Verdict
PASS | CONCERNS | FAIL

## Blocking issues

## Non-blocking improvements

## Missing questions

## Suggested edits
```
