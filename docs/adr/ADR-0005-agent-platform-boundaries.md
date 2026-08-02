# ADR-0005 — Agent Platform Boundaries

- Status: Accepted
- Date: 2026-08-02

## Context

The 5SOffice ecosystem contains a Webapp, a Customer Service Cockpit, AI Suite capabilities and a voucher project. Building overlapping platforms would increase cost and weaken governance.

## Decision

- Webapp owns customer and tenant channels.
- Customer Service Cockpit owns orchestration, guardrails, approval, handoff and operator administration.
- AI Suite owns agent definitions, domain workflows and reusable capability/tool adapters.
- Voucher & AI Credit Engine owns entitlements, usage rights and redemption.
- Web3 is an optional adapter, not a required customer journey.

## Consequences

Positive: clearer ownership, reuse, lower duplication and stronger traceability.

Trade-off: cross-repository contracts and coordinated release management are required.
