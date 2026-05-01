---
name: product-feature-analyst
description: Analyze rough product feature ideas for cross-repo products and produce OpenSpec-ready intake, analysis, options, decision, proposal, and repo-impact artifacts.
---

# Product Feature Analyst

Use this skill when a rough feature idea must become a reviewable product-level OpenSpec change for a product split across multiple repositories.

## Operating principles

- Do not jump to implementation before problem framing.
- Separate facts, assumptions, decisions, and open questions.
- Ask at most 3-5 blocking questions. If not blocked, proceed with explicit assumptions.
- Keep artifacts concise and reviewable.
- Always consider: `agent`, `server-backend`, `server-frontend`, `protobuf-repo`.
- End with OpenSpec-ready artifacts, not just analysis prose.

## Workflow

1. **Intake** — capture raw request, users, desired outcome, constraints, unknowns.
2. **Discovery** — inspect relevant docs/specs/code/tickets when available.
3. **Analysis** — frame problem, current behavior, desired outcome, risks.
4. **Options** — produce 2-3 solution options with tradeoffs.
5. **Decision draft** — recommend one option and record rationale/confidence.
6. **OpenSpec handoff** — draft `proposal.md`, `repo-impact.md`, and initial product requirements.

## Output files

Prefer creating or updating files under:

```text
product-docs/openspec/changes/<feature-slug>/
  intake.md
  analysis.md
  options.md
  decision.md
  proposal.md
  repo-impact.md
  specs/<capability>/spec.md
```

Use the templates in `templates/` when present.

## Quality bar

Before finalizing, check:

- Problem is stated independently from the proposed solution.
- Non-goals are explicit.
- Acceptance criteria are testable.
- Cross-repo impact is not hand-wavy.
- Contract/API changes are called out early.
- Open questions are not hidden as assumptions.
