# Stage Adaptation Guidelines

Use this reference to tailor the evaluation depth based on the lifecycle stage of the feature.

## 1. Ideation / Requirements Stage (PRD, Spec, Backlog Story)
* **Focus:** Problem validation, core user motivation, completeness of business rules, scope boundaries, and identifying unstated assumptions.
* **Output Emphasis:** Journey map, missing requirement questions, and edge cases to document before engineering starts.

## 2. Technical Design / Architecture Stage (API Specs, Schema Drafts)
* **Focus:** Entity state machine, data integrity, race conditions, idempotency, webhook retries, and failure recovery.
* **Output Emphasis:** State transition table, database invariant risks, and async event failure handling.

## 3. Implementation / Code Review Stage (Active PR, Existing Codebase)
* **Focus:** UI error states, validation logic, loading skeletons, transaction boundaries, and unhandled promise/exception paths.
* **Output Emphasis:** Line-level edge case vulnerabilities, missing loading/empty states, and missing rollback mechanisms.

## 4. Post-Launch / Optimization Stage (Live Feature Audit)
* **Focus:** User drop-off analysis, support ticket drivers, operational friction for internal teams, and performance bottlenecks.
* **Output Emphasis:** Streamlining recommendations, friction removal, and operational tooling gaps.
