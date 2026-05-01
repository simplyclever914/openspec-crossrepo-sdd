# Cross-Repo OpenSpec Workflow

## 1. Product change

Create a central change in the product docs repository:

```text
product-docs/openspec/changes/<feature-slug>/
```

Required artifacts:

1. `intake.md` — raw request and initial framing.
2. `analysis.md` — problem, users, current behavior, desired outcome, constraints.
3. `options.md` — 2-3 solution options with tradeoffs.
4. `decision.md` — selected option, rationale, assumptions, unresolved questions.
5. `proposal.md` — OpenSpec-style proposal.
6. `repo-impact.md` — affected repositories and implementation order.
7. `specs/**/*.md` — product-level requirements and scenarios.
8. `design.md` — cross-repo design and contract strategy.
9. `tasks.md` — orchestration checklist, not every repo's detailed task list.
10. `validation.md` — integration acceptance and rollout checks.

## 2. Review gates

Recommended gates:

- **Analysis gate:** problem is clear; assumptions and open questions are explicit.
- **Decision gate:** one option is selected; tradeoffs are recorded.
- **Repo-impact gate:** affected repos, contract changes, and implementation order are clear.
- **Spec gate:** acceptance criteria are reviewable and testable.
- **Implementation-readiness gate:** repo slices can be created without guessing.

## 3. Repo implementation slices

For each affected repository, create a local change:

```text
server-backend/openspec/changes/<feature-slug>-backend/
agent/openspec/changes/<feature-slug>-agent/
server-frontend/openspec/changes/<feature-slug>-frontend/
protobuf-repo/openspec/changes/<feature-slug>-contract/
```

Each repo slice must link to the parent product change and list implemented requirements/scenarios.

## 4. Contract-first order

If protobuf/API contracts change, the usual order is:

1. `protobuf-repo`
2. `server-backend`
3. `agent`
4. `server-frontend`

Frontend can often start against mocks, but merge should follow contract stabilization.

## 5. Archive order

Archive repo-level changes first. Archive the central product change last, after integration validation.
