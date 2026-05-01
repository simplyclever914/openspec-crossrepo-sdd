# OpenSpec Cross-Repo SDD

A lightweight, OpenSpec-based workflow for products split across multiple repositories.

It combines:

- **product-level OpenSpec** for feature intent, analysis, requirements, repo impact, and cross-repo validation;
- **repo-level OpenSpec slices** for implementation details close to code;
- **agent skills** for product analysis, review, and implementation planning;
- **MkDocs-friendly docs** for longer analysis, ADRs, and diagrams.

This is intentionally smaller than a full multi-agent methodology. It borrows the useful idea of role-based workflows from frameworks such as BMAD, but keeps OpenSpec as the canonical SDD layer.

## Repository layout

```text
skills/
  product-feature-analyst/       # turn rough ideas into analysis/options/OpenSpec handoff
  product-feature-reviewer/      # critique analysis before implementation
  repo-implementation-planner/   # create repo-local OpenSpec slices

openspec/schemas/
  product-crossrepo/             # heavy product-level flow
  repo-implementation-slice/     # lightweight implementation flow

docs/
  workflow.md
  openspec-integration.md
  agent-roles.md
  adoption-guide.md

scripts/
  validate-openspec-change.py
```

## Recommended topology

```text
product-docs/
  openspec/        # schema: product-crossrepo
  docs/            # MkDocs: long analysis, ADRs, diagrams

agent/
server-backend/
server-frontend/
protobuf-repo/
  openspec/        # schema: repo-implementation-slice
```

## Core idea

One cross-repo feature creates:

1. one **central product change** in `product-docs`;
2. one **implementation slice** in each affected repository.

The central change answers **what and why**. Repo slices answer **how this repo implements its part**.

## Quick start

1. Copy `openspec/schemas/product-crossrepo` into your product docs repo.
2. Set `openspec/config.yaml`:

```yaml
schema: product-crossrepo
```

3. Copy `openspec/schemas/repo-implementation-slice` into each code repo.
4. Set repo-level `openspec/config.yaml`:

```yaml
schema: repo-implementation-slice
```

5. Use the skills in `skills/` as AgentSkill packages or prompt/workflow references.
6. Add `scripts/validate-openspec-change.py` to CI to enforce required sections.

## Feature lifecycle

```text
intake → analysis → options → decision → proposal → repo-impact → specs → design → tasks → validation → archive
```

See:

- [docs/workflow.md](docs/workflow.md)
- [docs/adoption-guide.md](docs/adoption-guide.md)
- [docs/centralized-vs-hybrid.md](docs/centralized-vs-hybrid.md)

## License

MIT.
