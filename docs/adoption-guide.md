# Adoption Guide

This workflow is designed to be adopted gradually. Do not start by forcing every component repository to use a custom process.

## Recommended rollout

### Phase 1: Centralized product OpenSpec only

Start with one product/specs repository:

```text
product-docs/
  openspec/
    schema: product-crossrepo
```

For each cross-repo feature, create one central product change:

```text
product-docs/openspec/changes/<feature-slug>/
  intake.md
  analysis.md
  options.md
  decision.md
  proposal.md
  repo-impact.md
  specs/
  design.md
  slices/
    protobuf-repo.md
    server-backend.md
    server-frontend.md
    agent.md
  tasks.md
  validation.md
```

Component repositories do not need OpenSpec yet. Developers and agents work from the relevant `slices/<repo>.md` file.

PRs in component repos should link to:

- parent product change;
- relevant repo slice;
- implemented requirement/scenario.

This phase gives the team one source of truth without forcing repo-level process changes.

### Phase 2: Standard OpenSpec in component repositories

After the centralized flow proves useful, initialize normal OpenSpec in component repositories:

```text
agent/
server-backend/
server-frontend/
protobuf-repo/
  openspec/        # standard OpenSpec flow
```

Do not use the heavy `product-crossrepo` schema in component repos.

Use standard OpenSpec artifacts:

```text
proposal.md
specs/
design.md
tasks.md
```

Add a parent link convention to local `proposal.md`:

```md
## Parent Product Change

product-docs/openspec/changes/<feature-slug>

## Implements

- Requirement: ...
- Scenario: ...

## Local Scope

This repository implements ...

## Out of Scope

...
```

This keeps local implementation context near code while preserving the product change as the source of truth.

### Phase 3: Enforcement and automation

Add CI checks gradually:

1. Warning-only validation for product changes.
2. Required product-level validation before feature implementation starts.
3. PR template requiring product change and slice links.
4. Optional repo-level validation for standard OpenSpec changes.

Use `scripts/validate-openspec-change.py` as a starting point.

### Phase 4: Optional repo-specific customization

Only introduce custom repo-level schemas if a specific repository needs stronger local gates.

Most teams should be fine with standard OpenSpec in component repos.

## Decision matrix

| Stage | Product repo | Component repos | Best when |
|---|---|---|---|
| Phase 1 | Custom `product-crossrepo` | No OpenSpec, PR links only | Starting adoption, reducing friction |
| Phase 2 | Custom `product-crossrepo` | Standard OpenSpec | Teams want local implementation plans near code |
| Phase 3 | Custom + CI gates | Standard OpenSpec + PR checks | Process is stable and useful |
| Phase 4 | Custom | Optional custom repo schemas | Only for complex/high-risk repos |

## Recommendation

Start with Phase 1. Move to Phase 2 only after the team has used the centralized flow on real features and agrees the extra local structure is helpful.
