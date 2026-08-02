# ADR-0006 — Human Confirmation and Approval for Agent Actions

- Status: Accepted
- Date: 2026-08-02

## Context

AI agents may propose bookings, redemptions, messages or professional-domain outputs. Silent autonomous execution creates operational and governance risk.

## Decision

- All external write actions require explicit user confirmation at minimum.
- Tier 3 consequential actions require approval by an authorized human role.
- Approval must bind to the exact action parameters and expire when parameters materially change.
- Tools must reject missing, expired or mismatched approval tokens.
- The evidence record must identify the proposal, approver, timestamp, execution and outcome.

## Consequences

The user experience has additional steps, but the system gains accountability, reversibility and defensible evidence.
