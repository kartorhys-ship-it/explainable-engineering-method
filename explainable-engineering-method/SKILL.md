---
name: explainable-engineering-method
description: Apply EEM to engineering work that needs explicit requirements, traceable verification, and human understanding. Use when EEM is requested or a task specifically requires an explainable engineering workflow; ordinary coding questions do not require the full method.
---

# Explainable Engineering Method

## What this skill is for

Use EEM to keep four things connected:

1. The result the user wants.
2. The implementation that produces it.
3. The evidence that supports the result.
4. The human understanding needed to maintain it.

This is a v0.1 draft. Following the method does not prove that the method or the project is effective.

## How to apply it

- Read [the method](references/method.md) when the task needs EEM. Pick the relevant workflow in [workflows](references/workflows.md); do not run every workflow.
- Keep the user's actual request in view. A request for an explanation, review, or diagnosis does not automatically authorize implementation. A request to create a package does not authorize installing or activating it elsewhere.
- Inspect the project's instructions, current behavior, existing changes, and normal source locations before editing. EEM provides a way to link decisions and evidence; it does not require a new folder layout.
- Identify the desired outcome, scope, acceptance criteria, workflow mode, and rigor level. Make ordinary assumptions and continue. Ask only when a missing choice would materially change correctness, scope, or authority.
- Reuse an existing issue, change description, or short note as the Work Record when it already contains the needed information. Read [templates](references/templates.md) when creating or expanding a record. Read [examples](references/examples.md) when a concrete interpretation would help.
- Keep expected behavior separate from observed behavior. Link each material completion claim to the evidence that supports it. Say clearly when a check failed, was not run, or was inconclusive.
- Choose checks that match the claim and its risk. Do not require a unit test for every task or create checks that merely repeat the implementation.
- Treat human understanding as its own status. An assistant-written walkthrough is learning material; it does not prove that a person understands the system. If a required human check cannot happen yet, finish other authorized work and leave the check pending.
- Use the rigor guidance to decide whether independent review is useful. Do not create extra approval gates or delegate automatically. Delegation requires authorization from the session or applicable instructions.
- Read [the trial plan](references/trial-plan.md) when evaluating EEM itself. Do not rewrite the governing method after one isolated failure.

## Authority, stopping, and handoff

Choose implementation details within the agreed boundaries and the project's conventions. Explain a material trade-off and ask for a decision when it would change promised behavior or scope. Never weaken an acceptance criterion silently to make the result pass.

Continue safe, relevant work while uncertainty is being resolved. Stop the affected action when authorization is missing, a material product decision is unresolved, required evidence cannot be obtained, or another retry would repeat the same failure without a new hypothesis. Preserve partial results and name the exact missing input or capability. A blocked check does not prevent independent, authorized work from continuing.

In the final handoff, state what changed or was learned, which criteria were checked, what the evidence supports, the limits of that evidence, and the separate statuses for implementation, verification, human explanation, and release. Do not say that a release happened unless it actually happened.

## Scope

EEM does not choose one universal architecture, require new tools, grant deployment authority, or ask a person to memorize every line of code. Keep simple tasks simple. Use specialist practices when the project needs them; EEM is a coordination method, not a replacement for those practices.
