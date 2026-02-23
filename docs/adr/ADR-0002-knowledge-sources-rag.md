# ADR-0002: Knowledge Sources and RAG Classification

## Status
Accepted

## Context

AI features rely on retrieval-augmented generation (RAG) to provide accurate responses, particularly for legal and compliance guidance.

Incorrect or unverified sources introduce risks including misinformation, hallucination, and regulatory exposure.

A clear classification of knowledge sources is required.

## Decision

Knowledge sources are classified into three tiers:

### Tier 1 — Authoritative public sources
Examples:
- Government portals
- Official regulations
- Standards bodies

Characteristics:
- Read-only
- Globally shared
- Versioned

### Tier 2 — Tenant knowledge
Examples:
- Contracts
- Policies
- Internal documents

Characteristics:
- Tenant-scoped
- Not shared
- Access controlled

### Tier 3 — Derived AI artifacts
Examples:
- Summaries
- Checklists
- Insights

Characteristics:
- Traceable to original sources
- Regenerable
- Versioned

## RAG Rules

- Retrieval must respect tenant boundaries
- Legal outputs must cite Tier 1 sources
- Derived content must retain traceability

## Consequences

Positive:
- Reduced hallucination risk
- Explainable outputs
- ISO 42001 transparency support

Trade-offs:
- Additional indexing complexity
- Need for source validation workflows

## Follow-ups

- Source trust registry
- Document ingestion validation
- Source freshness monitoring
