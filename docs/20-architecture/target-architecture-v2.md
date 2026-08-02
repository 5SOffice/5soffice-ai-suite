# Target Architecture v2

## Context

The AI Suite supplies agent and domain capabilities. It does not duplicate the customer channel, orchestration cockpit or entitlement engine.

```text
Channels
  5SOffice Webapp | Tenant Portal | Operator Console
                         |
                         v
Special AI Customer Service Cockpit
  Conversation | Orchestration | Guardrails | Approval | Handoff
                         |
                         v
5SOffice AI Suite Capability Layer
  Agent registry | Workflow definitions | Tool adapters | Domain prompts
                         |
       +-----------------+------------------+
       |                 |                  |
       v                 v                  v
Knowledge Services   Business APIs    Voucher/Credit Engine
RAG + metadata       Booking/CRM/etc. Entitlement/redemption
       |                 |                  |
       +-----------------+------------------+
                         |
                         v
Evidence, audit, monitoring and governance services
```

## Logical components

1. **Agent Registry** — versioned definitions, capabilities, risk tier and ownership.
2. **Workflow Engine Interface** — state transitions and resumable business workflows.
3. **Tool Registry** — schemas, permission requirements, idempotency and risk classification.
4. **Knowledge Gateway** — tenant-scoped retrieval and source metadata.
5. **Policy Decision Point** — evaluates role, tenant, entitlement, purpose and action risk.
6. **Approval Service Interface** — human confirmation or operator approval.
7. **Evidence Writer** — records decisions, approvals and tool outcomes.
8. **Usage Meter** — records billable actions and credit consumption.
9. **Observability** — latency, errors, model/tool performance, cost and safety signals.

## Required architecture properties

- strict tenant scoping for every read and write;
- least privilege and short-lived tool credentials;
- idempotent business actions;
- clear separation between proposed and executed actions;
- no secret values in prompts or logs;
- model/provider abstraction;
- trace IDs across channel, cockpit, workflow, tool and evidence records;
- explicit data retention and deletion rules;
- graceful degradation and human fallback.

## Deployment sequence

1. Mock tool adapters and static approved knowledge.
2. Read-only booking availability integration.
3. Confirmed booking-request write integration.
4. Ticketing and human handoff.
5. Voucher/credit integration.
6. Additional tenant and SME capabilities.
