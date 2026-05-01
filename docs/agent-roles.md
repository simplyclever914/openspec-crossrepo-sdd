# Agent Roles

The workflow uses small, composable roles rather than a heavy multi-agent system.

## Product Feature Analyst

Turns rough input into structured product analysis and OpenSpec-ready artifacts.

Outputs:

- `intake.md`
- `analysis.md`
- `options.md`
- draft `proposal.md`
- draft `repo-impact.md`

## Product Feature Reviewer

Acts as a skeptical reviewer before engineering starts.

Checks:

- problem framing;
- hidden assumptions;
- missing users or edge cases;
- unclear acceptance criteria;
- repo-impact gaps;
- rollout/security/compatibility risks.

## Repo Implementation Planner

Creates a local implementation slice for a specific repository.

Outputs:

- local `proposal.md` with parent link;
- `design.md`;
- local `specs/**/*.md`;
- `tasks.md`;
- `validation.md`.

## Human ownership

Agents draft and critique. Humans approve decisions, tradeoffs, scope, and rollout risk.
