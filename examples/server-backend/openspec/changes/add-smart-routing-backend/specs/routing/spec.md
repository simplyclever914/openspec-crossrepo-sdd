# Local Specification: routing

## Parent requirement

## Requirement: Persist and apply routing policy

This repository SHALL persist routing policies and apply them when tasks are created.

### Scenario: backend fallback selection

GIVEN a routing policy exists and the preferred agent is unavailable
WHEN the backend schedules a task
THEN the backend selects the next eligible agent
