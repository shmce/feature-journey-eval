---
name: feature-journey-eval
description: Audits end-to-end user journeys, business process state lifecycles, and failure modes across any product or system domain. Produces a sequence map, state transition matrix, edge-case vulnerability audit, and operational readiness recommendations when explicitly invoked with $feature-journey-eval.
---

# Feature Journey & Business Process Evaluator

Perform comprehensive, end-to-end audits of product features, user journeys, and backend business process workflows across any domain (web, mobile, backend services, hardware/IoT, internal ops, or enterprise workflows).

## Invocation & Purpose

This skill is invoked explicitly (e.g. `$feature-journey-eval` or direct requests to evaluate a feature's journey or business process). It adapts across all product stages—from early PRDs and technical design to code reviews and post-launch audits.

## Core Evaluation Pillars

1. **Stage Adaptability**
   * Detect or infer the active stage (Ideation/PRD, Tech Architecture, Implementation/Code, or Live/Post-Launch).
   * Refer to [references/stage_adaptation.md](references/stage_adaptation.md) to calibrate feedback depth for that stage.

2. **The User Journey & Experience Arc**
   * Audit the full lifecycle from discovery/entry to completion and post-action feedback.
   * Check the 6 critical states: Empty, Happy Path, Loading/Async, Partial/Draft, Error/Validation, and Extreme/Edge cases.
   * Refer to [references/ux_journey_matrix.md](references/ux_journey_matrix.md) for cognitive friction and UX boundary checklists.

3. **The Business Process & State Machine**
   * Map all entity states, transition triggers, and terminal conditions.
   * Check for illegal state jumps, idempotency hazards (double submits, webhook retries), race conditions, and dangling states during external service downtime.
   * Refer to [references/state_machine_audit.md](references/state_machine_audit.md) for state completeness and auditability.

4. **Operational & Failure Resilience**
   * Uncover the "unhappy paths": network timeouts, expired credentials, payment reversals, inventory contention, or manual support intervention requirements.
   * Identify dead-ends where a user or internal operator gets permanently stuck without a clear recovery path.

## Output Structure

Format the evaluation cleanly and actionably:

```markdown
### 1. Executive Summary & Journey Health
* **Feature Scope & Assumed Stage:** [Short summary of the feature and current stage: PRD / Tech Spec / Code / Live]
* **Readiness Score:** [Ready to Ship / Needs Hardening / High Risk of Operational Failure]
* **Top Critical Vulnerability:** [Single most important blindspot or unhandled state]

### 2. End-to-End User Journey Flow
[Textual sequence or step-by-step path detailing discovery, input, execution, and confirmation, highlighting where friction or confusion occurs.]

### 3. Business Process & State Transition Matrix
| Current State | Trigger / Event | Next State | Guardrails & Idempotency | Failure / Fallback Path |
| :--- | :--- | :--- | :--- | :--- |
| `Draft` | User clicks Submit | `Pending_Validation` | Check required fields & auth | Remain in `Draft` with inline errors |
| `Processing` | Async worker finished | `Completed` | Idempotent transition key | Transition to `Failed_Retryable` + DLQ |

### 4. Edge Case & Failure Mode Matrix
| Category | Scenario / Failure Mode | User Impact | System / Ops Impact | Recommended Fix / Guardrail |
| :--- | :--- | :--- | :--- | :--- |
| **UX Friction** | User drops off halfway | Lost input data | Abandoned orphan records | Auto-save draft + resume link |
| **Concurrency** | Double-submit on slow network | Duplicate transaction | Financial/data duplication | Client debounce + Idempotency-Key |
| **Async / Ops** | Webhook dropped | Stuck in "Processing" | High support tickets | Reconcile cron / Dead-letter alert |

### 5. High-Impact Action Items
1. **[Critical / Must Fix]:** [Immediate fix before moving forward]
2. **[Important / Hardening]:** [Improvement for reliability or user experience]
3. **[Polish / Nice to have]:** [Friction reduction or operational convenience]
```
