# Centralized vs Hybrid OpenSpec

There are two recommended operating modes.

## Option A: Centralized OpenSpec

Use only the product/specs repository.

```text
product-docs/
  openspec/
    changes/<feature>/
      analysis.md
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

Component repositories do not have OpenSpec. Their PRs reference the product change and repo slice.

### Benefits

- Fastest adoption.
- One source of truth.
- No component-repo configuration.
- Good for teams that are new to SDD.
- Works well when product/architecture leads coordinate cross-repo work.

### Tradeoffs

- Repo-specific design/tasks are not stored next to code.
- Coding agents need to be given the relevant central slice as context.
- Local implementation knowledge may remain centralized rather than archived in each repo.

### Best for

- Initial rollout.
- Cross-repo features with moderate local complexity.
- Teams that want minimal process overhead.

## Option B: Hybrid OpenSpec

Use custom product-level OpenSpec at the top and standard OpenSpec in component repositories.

```text
product-docs/
  openspec/
    schema: product-crossrepo

agent/
server-backend/
server-frontend/
protobuf-repo/
  openspec/
    standard OpenSpec flow
```

The product change answers:

- what are we building;
- why;
- product requirements;
- affected repositories;
- cross-repo ordering;
- acceptance criteria;
- integration validation.

Repo-level standard OpenSpec answers:

- how this repository implements its part;
- local design;
- local requirements/scenarios;
- local tasks;
- local validation.

### Local proposal convention

Each repo-level OpenSpec change should include:

```md
## Parent Product Change

## Implements

## Local Scope

## Out of Scope

## Dependencies
```

### Benefits

- Product intent remains centralized.
- Implementation plans live close to code.
- Standard OpenSpec keeps repo adoption simple.
- Coding agents working inside a repo get local context naturally.
- Local specs can be archived into each repository's permanent knowledge base.

### Tradeoffs

- More files to maintain.
- Requires `openspec init` in component repos.
- Needs discipline to keep parent and local changes linked.

### Best for

- Mature adoption.
- Complex local implementations.
- Teams already using AI coding agents inside component repos.
- Repos with independent release cycles.

## Recommendation

Use a staged approach:

1. Begin with **centralized OpenSpec**.
2. Add **standard OpenSpec in component repos** only when the team wants local implementation context near code.
3. Avoid custom repo-level schemas unless a repository has a clear need for extra gates.

The default target architecture is:

```text
Top-level: custom product-crossrepo flow
Component repos: standard OpenSpec flow + parent link convention
```
