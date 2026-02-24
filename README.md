# 5SOffice AI Suite

**5SOffice AI Suite** is a multi-tenant AI SaaS suite for **SMEs in Vietnam** using serviced offices / coworking.  
It combines workspace services with AI-driven **operations**, **compliance**, and **growth** tools.

## What we build

A modular suite (8 modules) designed for SME reality (limited HR/Finance/Legal capacity):

1. **AI Meeting Scheduler & Optimizer** — scheduling + room booking with calendar integrations  
2. **AI Document Management & Automation** — OCR classification and workflow automation  
3. **AI HR Assistant** — CV screening assistance + onboarding workflows  
4. **AI Office Analytics & Predictive Maintenance** — usage insights + predictive maintenance  
5. **AI Content & Marketing Generator** — Vietnamese-first marketing content and campaign support  
6. **AI Customer Support Chatbot (Chat/Voice)** — internal/tenant support automation  
7. **AI Expense Tracker & Financial Insights** — receipt OCR + budgeting and forecasting  
8. **AI Legal Compliance Tracker & Advisor** — regulatory tracking, explainable impact, proactive alerts

See: `docs/10-products/projects-overview.md`

## Why it matters

SMEs often run lean and face:
- heavy admin workload
- unclear legal/compliance obligations
- limited HR/Finance capacity
- slow execution due to manual processes

This suite reduces operational friction, improves compliance safety, and enables growth — within a secure, isolated multi-tenant platform.

## Governance (ISO/IEC 42001-aligned)

This repository follows **AI governance principles aligned with ISO/IEC 42001 (AIMS)**:
- Bias & fairness awareness (especially HR use cases)
- Transparency & explainability (citations/effective dates for high-impact outputs)
- Human oversight & escalation paths (Legal/Finance/HR)
- Privacy & multi-tenant data isolation
- Accountability (logging/audit trail)
- Monitoring & continuous improvement

Key docs:
- Transparency: `docs/30-aims-iso42001/transparency-user-disclosures.md`
- Human oversight: `docs/30-aims-iso42001/human-oversight.md`
- AI use cases: `docs/30-aims-iso42001/ai-use-cases.md`

## Architecture decisions (ADRs)

We keep architectural decisions explicit and versioned:
- Tenant isolation: `docs/adr/ADR-0001-tenancy-isolation.md`
- Knowledge sources & RAG: `docs/adr/ADR-0002-knowledge-sources-rag.md`
- Logging & audit trail: `docs/adr/ADR-0003-logging-audit-trail.md`
- Model selection & prompt versioning: `docs/adr/ADR-0004-model-selection-prompt-versioning.md`

## Repository structure

- `docs/` — vision, product docs, governance (AIMS), architecture notes  
- `docs/adr/` — Architectural Decision Records  
- `apps/` — applications (created after pilot spec)  
- `packages/` — shared libraries (created after pilot)

## Current stage

Docs-first foundation is in place. Next steps focus on:
- roadmap/prioritization
- pilot specification (recommended pilot: Legal Compliance)
- MVP build and tenant rollout

See: `docs/10-products/roadmap-highlevel.md`

## Documentation index

### Overview
- Vision: `docs/00-overview/vision.md`
- Target customers: `docs/00-overview/target-customers.md`
- Differentiation: `docs/00-overview/differentiation.md`
- Glossary: `docs/00-overview/glossary.md`
- Contributing & workflow: `docs/00-overview/contributing-workflow.md`
- (Optional) Project leadership: `docs/00-overview/project-leadership.md`

### Product
- Modules overview (8 projects): `docs/10-products/projects-overview.md`
- Roadmap (high-level): `docs/10-products/roadmap-highlevel.md`
- Pricing & packaging (hypothesis): `docs/10-products/pricing-packaging.md`

### Architecture
- Infrastructure sizing / deployment notes: `docs/20-architecture/infra.md`

### AIMS (ISO/IEC 42001)
- AI use case inventory: `docs/30-aims-iso42001/ai-use-cases.md`
- Transparency & user disclosures: `docs/30-aims-iso42001/transparency-user-disclosures.md`
- Human oversight policy: `docs/30-aims-iso42001/human-oversight.md`

### ADRs
- ADR-0001 Tenancy isolation: `docs/adr/ADR-0001-tenancy-isolation.md`
- ADR-0002 Knowledge sources & RAG: `docs/adr/ADR-0002-knowledge-sources-rag.md`
- ADR-0003 Logging & audit trail: `docs/adr/ADR-0003-logging-audit-trail.md`
- ADR-0004 Model selection & prompt versioning: `docs/adr/ADR-0004-model-selection-prompt-versioning.md`

### Security & Privacy
- Security baseline: `docs/40-security-privacy/security-baseline.md`
- Privacy baseline: `docs/40-security-privacy/privacy-baseline.md`
- Threat modeling: `docs/40-security-privacy/threat-modeling.md`

### Operations
- Environments: `docs/50-operations/environments.md`
- Runbooks: `docs/50-operations/runbooks.md`
- SLA/SLO (pilot baseline): `docs/50-operations/sla-slo.md`

## Origin & project lead

**Nguyễn Đăng Quang** conceived the initial idea for 5SOffice AI Suite and leads the project end-to-end, including product direction, AI governance (ISO/IEC 42001), and quality control of architecture decisions (ADRs).
