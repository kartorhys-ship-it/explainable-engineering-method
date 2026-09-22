---
name: explainable-engineering-method
description: Apply EEM to engineering work that needs explicit requirements, traceable verification, and human understanding. Use when EEM is requested or a task specifically requires an explainable engineering workflow; ordinary coding questions do not require the full method.
---

# Explainable Engineering Method

## Purpose

Keep the requested engineering outcome, implementation, verification evidence, and required human understanding aligned. Apply a proportional process using existing project artifacts where possible.

This is a v0.1 draft. Do not claim the method or a project is validated merely because these instructions were followed.

## Required operating rules

- Read [the method](references/method.md) when applying EEM to project work. Select the relevant mode in [workflows](references/workflows.md); do not execute every mode.
- Preserve the user's actual request type. An explanation, review, or diagnosis does not authorize implementing the findings. Implement when requested. Package creation does not authorize installation or activation elsewhere.
- Inspect relevant project instructions, current behavior, and existing changes before editing. Use established source and document locations. EEM supplies links and acceptance conditions, not a mandatory repository layout.
- Identify the outcome, scope, acceptance criteria, mode, and rigor level. Infer routine details from context and proceed. Ask only when a missing choice materially affects correctness, scope, or authority.
- Use an existing issue, change description, or brief note as the Work Record. Read [templates](references/templates.md) only when creating or extending a record. Read [examples](references/examples.md) when a concrete interpretation is needed.
- Keep intended behavior distinct from observed behavior. Link each material completion claim to relevant evidence, and report checks that failed, were not run, or were inconclusive.
- Select verification by the claim and risk. Do not require unit tests for every task or create checks that merely repeat the implementation.
- Treat human explanation as a separate status. An assistant-generated walkthrough does not prove a human understands. When a human check is required but no response is available, finish other authorized work and report that check as pending.
- Use the rigor policy to decide whether independent review is needed; do not automatically spawn agents or create extra approval gates. Delegation requires authorization from the session or applicable instructions.
- Read [the trial plan](references/trial-plan.md) when assessing EEM itself. Do not silently rewrite the governing method after a single task failure.

## Autonomy, stopping, and handoff

Choose implementation details within the agreed contracts and existing conventions. Surface material trade-offs; request a decision if the choice would alter a promised behavior or scope. Never silently weaken acceptance criteria to make a result pass.

Continue safe, relevant work while resolving uncertainty. Stop the affected action when authorization is missing, a material product decision is unresolved, required evidence cannot be obtained, or another retry would repeat the same failure without a new hypothesis. Preserve partial results and identify the precise missing input or capability. Do not use a verification blocker as a reason to abandon independent, authorized work.

The final handoff states: what changed or was learned; acceptance results; evidence and its limits; implementation, verification, and explanation statuses; and any remaining action with its owner. Do not claim release occurred unless it actually occurred.

## Scope boundaries

EEM does not select a universal architecture, mandate new tools, grant deployment authority, or require the human to memorize every line of code. A simple task should stay simple. Apply specialized domain practices where they are relevant, without representing this method as a substitute for them.
