# Integration Contracts

This document defines minimum logical contracts. Concrete OpenAPI or event schemas should be created during implementation.

## Common request context

Every request must carry:

- `correlation_id`;
- `tenant_id` where applicable;
- authenticated `actor_id` and role;
- channel and conversation identifiers;
- requested purpose;
- locale;
- agent and workflow versions.

## Cockpit to AI Suite

### Start or continue workflow

Input: intent, context, authorized tenant scope and supplied artifacts.

Output: workflow state, proposed response, required confirmations, candidate tools, evidence references and escalation status.

## AI Suite to Booking API

Minimum operations:

- search locations/resources;
- query availability;
- quote or calculate applicable entitlement;
- create booking request with idempotency key;
- retrieve booking status;
- cancel subject to policy.

## AI Suite to Voucher & Credit Engine

Minimum operations:

- list eligible entitlements;
- preview redemption;
- reserve entitlement;
- confirm redemption after business transaction;
- release failed or expired reservation;
- retrieve usage ledger.

## AI Suite to Knowledge Gateway

Minimum operations:

- retrieve by tenant, domain and purpose;
- return citation/source ID, effective date and access classification;
- reject cross-tenant retrieval;
- support content withdrawal and re-indexing.

## Event model

Recommended events:

- `agent.workflow.started`;
- `agent.action.proposed`;
- `agent.action.approved`;
- `agent.tool.executed`;
- `agent.workflow.completed`;
- `agent.workflow.failed`;
- `agent.handoff.created`;
- `entitlement.reserved`;
- `entitlement.redeemed`;
- `entitlement.released`.

Events must avoid raw sensitive content unless explicitly required and protected.
