# 5SOffice AI Suite

**AI agents and digital services for SME tenants.**

5SOffice AI Suite is being repositioned from a broad collection of eight standalone AI applications into a shared, multi-tenant **AI Agent capability platform** for SMEs using 5SOffice and related business services.

The project is designed to work with:

- **5SOffice Webapp** as the customer and tenant channel;
- **Special AI Customer Service Cockpit** as the AI orchestration, guardrail, approval and administration layer;
- **5SOffice Voucher & AI Credit Engine** as the entitlement, quota and redemption layer;
- **HQC AI / AIMS governance assets** for governance, evidence and expert escalation.

## Product direction

```text
5SOffice Webapp / Tenant Portal
              |
              v
Special AI Customer Service Cockpit
        (AI Orchestrator)
              |
   +----------+----------+----------------+
   |          |          |                |
Office     Admin     Compliance        Growth
Agent      Agent       Agent            Agent
   |          |          |                |
   +----------+----------+----------------+
              |
    Shared Agent Capability Platform
              |
 Knowledge / Tools / Approval / Audit / Usage
              |
 Voucher & AI Credit Engine / Business APIs
```

## Agent portfolio

### 1. 5SOffice Tenant Agent — first MVP

The first production target. It assists tenants and customers with:

- service and policy questions;
- meeting-room and workspace availability;
- booking requests;
- reception and operational requests;
- voucher and AI-credit balance checks;
- voucher redemption;
- meeting summaries and basic administrative outputs;
- escalation to sales, support or reception staff.

### 2. SME Administrative Agent

Creates and manages common SME administrative work products, including meeting minutes, notices, payment requests, onboarding packs, document classification and deadline reminders.

### 3. SME Compliance Agent

Supports structured compliance and ISO-readiness workflows, including intake, gap checklists, implementation plans, evidence requests and expert escalation. High-impact or professional conclusions always require human review.

### 4. SME Growth Agent

Executes repeatable marketing workflows rather than only generating isolated text: campaign briefs, channel plans, content reuse, publication schedules and performance follow-up.

### 5. SME Management Agent — later phase

Produces management summaries and decision queues from authorized business data. This capability requires broader integrations and is not part of the first MVP.

## Shared platform capabilities

Every agent must use common platform services:

- tenant workspace and tenant isolation;
- identity, role and permission checks;
- knowledge sources and RAG with source metadata;
- tool registry and action authorization;
- human approval for consequential actions;
- immutable-enough audit and evidence records;
- prompt, model and policy versioning;
- usage metering, quotas and billing integration;
- safety, privacy and escalation controls.

## MVP scope

The first MVP is **5SOffice Tenant Agent**, limited to a small set of reliable end-to-end journeys:

1. answer 5SOffice service and policy questions;
2. find an appropriate meeting room or workspace;
3. create a booking request after explicit confirmation;
4. create a reception/support request;
5. check and redeem eligible vouchers or credits;
6. generate a meeting summary from user-provided content;
7. transfer the conversation to a human operator.

See:

- `docs/00-overview/product-direction-v2.md`
- `docs/10-products/agent-portfolio.md`
- `docs/10-products/mvp-tenant-agent.md`
- `docs/20-architecture/target-architecture-v2.md`
- `docs/20-architecture/integration-contracts.md`
- `docs/30-aims-iso42001/agent-governance-baseline.md`
- `docs/60-roadmap/implementation-roadmap-v2.md`

## Current stage

This repository remains docs-first. The next milestone is an approved MVP specification and API contract, followed by a thin vertical slice connected to the Webapp and Customer Service Cockpit.

## Non-goals

- Building eight independent SaaS products at the same time.
- Replacing the Customer Service Cockpit orchestration layer.
- Giving agents unrestricted access to tenant systems.
- Autonomous legal, financial, HR or compliance decisions.
- Building a generic chatbot without business actions and evidence.

## Governance

The platform follows ISO/IEC 42001-aligned principles: accountability, human oversight, traceability, risk-based controls, transparency, data protection and continual improvement. Alignment does not by itself constitute certification or conformity.

## Project owner

**Nguyễn Đăng Quang** — Project Owner and Concept Creator; responsible for product direction, AI governance and quality review.

## License

Retain the existing repository license unless the project owner approves a change.
