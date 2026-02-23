# ADR-0004: Model Selection and Prompt Versioning

## Status
Accepted

## Context

AI capabilities rely on external models and evolving prompt strategies.  
Uncontrolled changes may impact reliability, consistency, and compliance.

Versioning is required.

## Decision

The platform adopts:

### Model selection policy
- Multiple providers supported
- High-impact tasks prefer more reliable models
- Model usage recorded in logs

### Prompt versioning
- Prompts stored as versioned artifacts
- Changes documented
- Rollback supported

### Evaluation
- Key prompts require evaluation before release
- Regression checks for critical workflows

## Consequences

Positive:
- Reproducibility
- Controlled evolution
- Reduced risk of silent behavior changes

Trade-offs:
- Operational overhead
- Need for prompt governance

## Follow-ups

- Prompt registry
- Evaluation datasets
- Release checklist
