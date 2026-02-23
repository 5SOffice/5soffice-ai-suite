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

## Project lead

This initiative is led by **Nguyễn Đăng Quang**, overseeing product direction, governance alignment (ISO/IEC 42001), and delivery quality.
