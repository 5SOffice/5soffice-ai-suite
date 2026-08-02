# Agent Governance Baseline

## Purpose

Provide minimum governance controls for every production agent and workflow.

## Agent record

Each agent must have a versioned record containing:

- owner and accountable business function;
- intended purpose and users;
- prohibited uses;
- data categories and integrations;
- model and tool dependencies;
- risk classification;
- human oversight design;
- performance and safety metrics;
- deployment and rollback status;
- review date.

## Risk tiers

- **Tier 1 — Informational:** approved-source answers, no external write action.
- **Tier 2 — Operational:** reversible business action after user confirmation.
- **Tier 3 — Consequential:** material impact or professional domain; human approval is mandatory.
- **Tier 4 — Prohibited or unsupported:** workflow is blocked.

## Mandatory controls

1. Purpose and access validation.
2. Tenant isolation.
3. Grounding and source controls for knowledge answers.
4. Explicit confirmation before write actions.
5. Human review for consequential outputs.
6. Tool allowlists, schemas and least privilege.
7. Prompt, policy and model versioning.
8. Audit/evidence records with trace IDs.
9. Incident, override and rollback procedures.
10. Periodic performance, bias, privacy and security review as applicable.

## Evidence minimum

For an executed action, retain as permitted:

- normalized user intent;
- policy outcome;
- proposed action and key parameters;
- confirmation or approval identity and timestamp;
- tool request/result identifiers;
- final status and error information;
- agent, prompt, model and tool versions;
- source references used for material decisions.

Do not log secrets, full credentials or unnecessary personal data.

## Transparency

Users must be informed that they are interacting with AI, what the agent can and cannot do, when a human is involved and how to challenge or correct a result.
