# feature-journey-eval

An end-to-end user journey and business process evaluation skill for Codex.

Audits feature workflows across user experience, state machine transitions, concurrency risks, async job boundaries, and operational failure modes.

## Key Features

- **Stage-Adaptive:** Calibrates its analysis whether evaluating early PRD concepts, technical architecture & API specs, active code implementations, or live post-launch features.
- **Domain Agnostic:** Works across consumer web/mobile, B2B workflows, internal tooling, async event-driven systems, IoT/hardware interfaces, and financial/data pipelines.
- **State Transition Matrix:** Audits entity lifecycles, transition triggers, guardrails, illegal state jumps, and fallback paths.
- **Edge-Case & Failure Mode Analysis:** Catches double-submits, dropped webhooks, race conditions, partial-state dropouts, and dangling records.
- **Prioritized Action Plan:** Delivers prioritized recommendations (Critical, Hardening, Polish) with clear remediation steps.

## Installation

Clone or copy into your Codex skills directory:

```bash
git clone https://github.com/shmce/feature-journey-eval.git ~/.codex/skills/feature-journey-eval
```

## Usage

This skill is designed for explicit invocation:

```text
$feature-journey-eval Here is our plan for a multi-step user onboarding flow with phone OTP verification and account linking. What are the edge cases and business process gaps?
```

## Structure

```text
feature-journey-eval/
├── SKILL.md                          # Core instructions and evaluation structure
├── agents/
│   └── openai.yaml                   # Skill metadata and explicit invocation policy
└── references/
    ├── stage_adaptation.md           # How to calibrate analysis for PRD, Tech Spec, Code, or Live stages
    ├── state_machine_audit.md        # State transitions, idempotency, and concurrency rules
    └── ux_journey_matrix.md          # 6 critical user journey states & cognitive friction checklist
```
