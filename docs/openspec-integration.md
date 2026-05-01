# OpenSpec Integration

## Product-level schema

Use `product-crossrepo` only in the product docs/specs repository.

```yaml
# product-docs/openspec/config.yaml
schema: product-crossrepo
```

This schema enforces the heavier flow:

```text
intake → analysis → options → decision → proposal → repo-impact → specs → design → tasks → validation
```

## Repo-level schema

Use `repo-implementation-slice` inside implementation repositories.

```yaml
# server-backend/openspec/config.yaml
schema: repo-implementation-slice
```

This schema stays lightweight:

```text
proposal → design → specs → tasks → validation
```

## MkDocs integration

Keep long-form analysis in MkDocs when useful, but include a short distilled `analysis.md` in the OpenSpec change.

Recommended links:

```md
## Long-form docs

- Feature analysis: ../../docs/features/<feature-slug>.md
- ADRs: ../../docs/adr/
- Diagrams: ../../docs/diagrams/
```

Do not make OpenSpec depend only on external links. The change folder should contain enough summary for reviewers and AI agents to understand the feature.

## CI enforcement

Use `scripts/validate-openspec-change.py` in pull requests to check required files and headings.
