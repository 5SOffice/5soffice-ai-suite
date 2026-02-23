# Glossary

This glossary defines common terms used in the 5SOffice AI Suite repository.

## Core terms

- **5SOffice AI Suite**: A multi-tenant AI SaaS suite for SMEs using serviced offices, combining operational, compliance, and growth tools.
- **Tenant**: A customer organization (SME) using the platform. Tenant data must remain isolated from other tenants.
- **Multi-tenant isolation**: Architectural controls ensuring no cross-tenant data leakage at application, data, and AI layers (see ADR-0001).
- **AIMS**: AI Management System (ISO/IEC 42001). Governance framework for managing AI risks, transparency, oversight, and continuous improvement.
- **High-impact domain**: Use cases where AI output may significantly affect legal compliance, finance/tax decisions, or employment decisions (see human-oversight policy).
- **Human oversight**: Rules requiring user confirmation, review, and escalation paths for medium/high-impact AI outputs.

## AI / Knowledge terms

- **LLM**: Large Language Model used for conversational and generative capabilities.
- **RAG**: Retrieval-Augmented Generation. AI answers using retrieved documents as grounding context (see ADR-0002).
- **Tier 1 sources**: Authoritative public sources (e.g., official regulations). Globally shared and read-only.
- **Tier 2 sources**: Tenant documents (contracts, policies). Tenant-scoped and access controlled.
- **Tier 3 artifacts**: Derived outputs (summaries/checklists) that remain traceable to original sources.
- **Prompt versioning**: Managing prompts as versioned artifacts with change control and rollback capability (see ADR-0004).

## Operations terms

- **RBAC**: Role-Based Access Control. Restricts access by role within a tenant (admin/user/finance/HR).
- **Audit trail**: Records of AI interactions and metadata supporting accountability and investigations (see ADR-0003).
- **Escalation**: A workflow that routes high-impact questions to human support/consultants.
