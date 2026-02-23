# ADR-0001: Multi-tenant Isolation

## Status
Accepted

## Context

5SOffice AI Suite is a multi-tenant SaaS platform serving SMEs operating within serviced office environments.

Tenant data must remain strictly isolated to:
- Protect customer confidentiality
- Prevent cross-tenant leakage in AI outputs
- Support privacy and regulatory compliance
- Enable ISO/IEC 42001 (AIMS) governance and auditability

AI features introduce additional risks because retrieval, prompts, and generated outputs may combine multiple data sources.

Therefore, tenant isolation must be enforced across the entire platform stack.

## Decision

The platform enforces tenant isolation at multiple layers:

### Application layer
- Every request must include tenant context (tenant_id)
- Middleware enforces tenant scope before any data access

### Data layer
- Tenant-scoped storage for operational data
- Shared global corpora allowed only for public authoritative sources (e.g. laws, regulations)

### AI / RAG layer
- Retrieval indexes must be tenant-scoped by default
- Global knowledge bases are read-only
- Generated outputs must never include other tenants’ data

### Logging & audit
- All AI interactions log tenant_id
- Versioning of prompts/models is captured for traceability

## Consequences

Positive:
- Strong privacy guarantees
- Clear compliance posture
- Supports ISO 42001 accountability and transparency
- Enables enterprise customers

Trade-offs:
- Increased engineering complexity
- Requires strict testing and monitoring
- More careful design of shared knowledge layers

## Follow-ups

- Define tenant-aware logging standard
- Define RAG source classification (tenant vs global)
- Add automated isolation tests
- Document data retention per tenant
