# Roadmap (High-level)

This roadmap describes the phased plan for building 5SOffice AI Suite as a multi-tenant AI SaaS platform for SMEs.

## Guiding principles
- Docs-first, governance-first (ISO/IEC 42001 aligned)
- Build one pilot end-to-end before expanding to the full suite
- Multi-tenant isolation is non-negotiable
- High-impact AI (legal/finance/HR) must include human oversight and transparency

## Phases

### Phase 0 — Setup (Done)
- GitHub org/profile
- Central repository
- Repo visibility strategy

### Phase 1 — Foundation: Docs + Governance (Done, with ongoing polish)
- Vision and product overview (8 modules)
- AIMS entry point (AI use cases)
- ADR backbone (tenancy, sources/RAG, logging, model/prompt versioning)

### Phase 2 — Product Definition (Next)
**Goal:** clarify priorities, success metrics, and packaging before writing pilot specs.
Deliverables:
- Target personas and key problems
- Success metrics (KPIs/OKRs)
- Packaging and pricing hypothesis
- Confirm pilot scope and “definition of done”

### Phase 3 — Pilot Design (Next)
**Goal:** design one pilot product with clear UX flows, constraints, and evaluation plan.
Pilot candidate (recommended): **AI Legal Compliance Tracker & Advisor**
Deliverables:
- Pilot spec v1 (user journeys, screens, constraints)
- Data flow design (RAG + alerts)
- Human oversight rules (high impact)
- Evaluation plan (accuracy, hallucination, satisfaction)

### Phase 4 — MVP Build (Pilot implementation)
**Goal:** ship a working MVP to staging/internal use.
Deliverables:
- `apps/legal-compliance` created
- Auth + tenant context middleware (minimum “spine”)
- Tier-1 legal sources ingestion + RAG Q&A with citations
- Alerts (email/Zalo) + subscriptions
- Logging/audit trail per ADR-0003

### Phase 5 — Pilot Rollout (Real tenants)
**Goal:** validate value with 5–20 tenants and measure outcomes.
Deliverables:
- Tenant onboarding process
- Feedback loop (tickets + usage analytics)
- Pilot report and go/no-go decision

### Phase 6 — Platformization (Spine for the suite)
**Goal:** convert MVP into reusable platform components.
Deliverables:
- Shared packages: auth/rbac, notifications, logging, billing, evaluation
- Observability and runbooks
- Hardened governance and security baselines

### Phase 7 — Expand to the “Core Trio”
**Goal:** launch 2–3 modules with fastest ROI and cross-sell potential.
Recommended order:
1) Customer Support Chatbot (chat/voice)
2) Content & Marketing Generator
3) Document Automation (OCR workflows)

### Phase 8 — Full Suite (8 modules)
- HR Assistant
- Expense Insights
- Scheduler
- Office Analytics & Predictive Maintenance (IoT)

### Phase 9 — Certification-ready (Optional)
- AIMS internal audit cycle (ISO/IEC 42001)
- Management review cadence
- Mature risk register and incident handling
- Optional alignment with ISO/IEC 27001/27701 for data governance

## Pilot definition of success (initial)
- Measurable reduction in time spent tracking legal/compliance updates
- High trust signals: citations, effective dates, clear limitations
- Low critical error rate for high-impact outputs
- Clear tenant value leading to retention/upsell interest
