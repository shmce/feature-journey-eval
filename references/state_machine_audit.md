# State Machine & Business Lifecycle Audit

Use this reference when evaluating entity lifecycles, state transitions, async background jobs, and operational invariants.

## Core State Machine Principles

1. **State Completeness & Exhaustion**
   * Enumerate every possible state an entity can occupy (e.g. `Draft`, `Pending_Approval`, `Processing`, `Active`, `Failed`, `Suspended`, `Archived`).
   * Verify that every state has at least one valid exit transition, except explicitly terminal states.

2. **Transition Triggers & Authorization Guardrails**
   * Who or what triggers each transition? (User action, system cron, external webhook, admin override).
   * What guardrails prevent illegal transitions? (e.g., transitioning from `Cancelled` directly to `Fulfilled`).

3. **Idempotency & Concurrency**
   * **Duplicate Invocations:** If a user double-clicks or an external webhook retries 5 times, is the transition safe? (Use idempotency keys or database-level optimistic locking).
   * **Race Conditions:** Two users or background processes editing the same entity simultaneously.

4. **Failure Recovery, Retries & Dead-Letter States**
   * If an intermediate step fails (e.g., third-party API timeout while transitioning `Payment_Pending` → `Paid`), does the system leave the entity in a hanging state?
   * Define automatic recovery / retry logic vs. manual support intervention.

5. **Auditability & Observability**
   * Does each critical state transition record: `from_state`, `to_state`, `actor_id`, `timestamp`, and `reason`?
