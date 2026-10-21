# UX Journey & Boundary Audit Guide

Use this reference when evaluating user flows, interface states, friction points, and edge-case handling.

## The 6 Critical Journey States

For any feature or screen, evaluate how the user experiences:

1. **First-Time / Empty State (Zero-Data):** What does the screen look like before any data exists? Is there guidance or a clear call to action?
2. **Happy Path (Nominal):** The standard frictionless path when all data is valid, systems respond immediately, and the user follows expected intent.
3. **Loading / Asynchronous State:** Is loading instant, skeleton-based, or blocked with spinners? Does the user know background processing is underway?
4. **Partial / Incomplete State:** The user starts a workflow, drops out halfway, or saves a draft. Can they resume seamlessly without losing progress?
5. **Error & Validation State:** Inline validation vs. blocking modals. Are errors actionable with clear recovery paths ("Credit card expired - update here") rather than generic ("Operation failed")?
6. **Extreme / High-Volume State:** What happens with 10,000 items in a list, extremely long text inputs, or slow 3G network connections?

## Friction & Cognitive Load Checklist

* **Step Reduction:** Can any field or step be deferred, inferred, or auto-populated?
* **Reversibility / Undo:** Can destructive actions be undone easily, or do they require unnecessary confirmation dialogues that cause fatigue?
* **Feedback Clarity:** Does the user receive immediate, unambiguous confirmation of state changes?
