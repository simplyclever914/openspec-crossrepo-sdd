---
name: repo-implementation-planner
description: Create lightweight repo-level OpenSpec implementation slices from a parent product-level cross-repo OpenSpec change.
---

# Repo Implementation Planner

Use this skill inside a code repository (`agent`, `server-backend`, `server-frontend`, `protobuf-repo`) after the product-level OpenSpec change is approved.

## Inputs

- Parent product change path or URL.
- Target repository name.
- Relevant product requirements/scenarios.
- Contract versions or API/protobuf changes if any.

## Workflow

1. Read parent `proposal.md`, `repo-impact.md`, relevant `specs/**/*.md`, and `design.md` if present.
2. Identify only this repository's responsibility.
3. Create local OpenSpec change under:

```text
openspec/changes/<feature-slug>-<repo-suffix>/
```

4. Generate:

```text
proposal.md
design.md
specs/<capability>/spec.md
tasks.md
validation.md
```

5. Link every local requirement back to parent product requirement/scenario.

## Do not

- Re-run product discovery locally.
- Invent product scope that is absent from the parent change.
- Duplicate every central requirement; include only local responsibilities.
- Ignore mixed-version compatibility.

## Required local proposal sections

```md
## Parent product change
## Implements requirements
## Local scope
## Out of scope
## Dependencies
```
