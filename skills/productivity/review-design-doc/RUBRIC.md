# Design Doc Rubric

Baseline structure for a design doc at this org. Templates won't always have every section — use this as a mental checklist. Flag a missing section **only when its absence creates ambiguity, risk, or an unanswered question** (see SKILL.md, "only-when-it-matters rule").

## Summary

High-level TL;DR. Why the change matters, what it does, what's proposed. Should link to the Background section for the longer story.

**Watch for**: a Summary that reads like a feature description but doesn't say *why now* or *why this approach*.

## Requirements

All requirements including non-functional. May link to a PRD, or be inline for technical-only docs. Dependencies and prerequisites should be called out separately.

### Goals
Concise bullets. What this design is committing to deliver.

### Non-Goals
Concise bullets. **Defends against scope creep.** Frequently missing — flag when scope feels fuzzy.

### Non-Functional Requirements (optional)
Performance, availability, compliance, etc. Often inherited from the PRD. Flag if NFRs are obviously load-bearing for the design but unstated (e.g., a real-time feature with no latency target).

### Prerequisites & Dependencies
What needs to exist first? What's owned by another team? Flag when the design depends on unowned/unscoped work.

## Design

The engineering approach. Multiple proposals are fine early; once a design is chosen, alternatives move to Alternatives Considered.

### System Context and Architecture
How this fits the broader ecosystem. Block / flow / sequence diagrams help.

### Data Flow & Storage (optional)
Use when data movement or persistence is non-trivial.

### APIs (optional)
New or modified endpoints, kept high-level.

### Pseudocode (optional)
For load-bearing algorithms or critical paths.

### Security Considerations (optional)
PII, public surface area, auth boundaries.

### Risks
Tech debt, unknowns, things the design choices explicitly trade away. **Flag when missing — risks-shaped silence is itself a risk.**

## Alternatives Considered (optional)

Designs that were considered and rejected, with reasons. Flag when the design has obvious viable alternatives that aren't discussed (e.g., "why build instead of buy?", "why event-driven instead of polling?").

## Testing Plan (optional)

How will you know it works? How will you know it stops working?

### Functional Testing
Unit, integration, E2E, contract, manual. Include CI/CD integration if relevant.

### Performance & Load Testing
Expected load, simulation strategy, blast radius on adjacent systems.

### Security Testing
Where applicable.

## Operations (optional)

How is this launched, monitored, troubleshot?

### Release Plan
Flags, phased rollout, canary. Flag when missing on anything user-facing.

### System Observability Updates
Logging, dashboards, alerts — from both engineering and support perspectives.

### Operational Support Considerations
Runbooks, new or updated.

## NLS / Localization

Multiple languages and regions, formats, UI fit. Flag for user-facing surfaces; usually skip for internal tools.

## Background

Detailed context anyone from any team can read. Why the gap exists.

## References (optional)

PRDs, related design docs, external articles.

## Sign Off

Reviewed by a staff engineer or equivalent, with feedback addressed. Flag when the doc is presented as final but has no named reviewer.
