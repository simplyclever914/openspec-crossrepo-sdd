# Specification: routing

## Requirement: Smart routing policy

The system SHALL route tasks according to the configured routing policy.

### Scenario: preferred agent unavailable

GIVEN a preferred agent is unavailable
WHEN a task is created
THEN the system falls back to the next eligible agent
