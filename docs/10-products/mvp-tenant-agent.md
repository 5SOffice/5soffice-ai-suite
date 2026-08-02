# MVP Specification — 5SOffice Tenant Agent

## Objective

Deliver one trustworthy conversational agent that can answer, recommend and complete selected 5SOffice tenant-service workflows.

## MVP users

- authenticated tenant user;
- prospect or website visitor with limited anonymous capability;
- reception/support operator;
- system administrator.

## In-scope journeys

### J1 — Service and policy question

The agent answers from approved 5SOffice sources, includes source metadata where useful and escalates when the source is missing or ambiguous.

### J2 — Find a meeting room

The agent gathers location, date, time, capacity and equipment requirements; queries availability; returns eligible options and pricing or entitlement information.

### J3 — Create a booking request

The agent presents a final booking summary, obtains explicit user confirmation, invokes the booking API and returns a booking reference.

### J4 — Reception or support request

The agent collects category, site, urgency and description, creates a ticket and provides status information.

### J5 — Voucher or credit check and redemption

The agent shows eligible rights, explains conditions, obtains confirmation, creates a redemption order and links it to the business service transaction.

### J6 — Meeting summary

The user supplies text, transcript or supported file. The agent returns a summary, decisions, owners and due dates. It must clearly mark inferred or missing information.

### J7 — Human handoff

The agent transfers the case with a concise conversation summary, user consent where required and relevant evidence references.

## Excluded from MVP

- payment execution;
- autonomous contract acceptance;
- unrestricted email or messaging actions;
- legal or financial advice;
- broad third-party system integrations;
- on-chain wallet requirement.

## Acceptance criteria

- All write actions require explicit confirmation.
- A user cannot access another tenant's data or entitlements.
- Every action has a stable correlation ID and final status.
- Tool failures are visible and do not produce false success messages.
- Knowledge answers identify source and last-updated metadata when available.
- Human operators can review escalated cases and the relevant action history.
- The MVP supports Vietnamese as the primary language.

## Pilot metrics

- task completion rate;
- booking and ticket success rate;
- handoff rate and handoff quality;
- grounded-answer rate;
- operator time saved;
- customer satisfaction;
- policy or privacy incidents;
- cost per completed task.
