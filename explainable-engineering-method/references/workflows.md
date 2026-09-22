# EEM workflows

Use the rules in [method.md](method.md), then choose the workflow that matches the work in front of you. Do not run every workflow. Mix them only when the task really needs it; for example, a migration can include a feature change, and an incident can lead to a later bug fix.

Each workflow has an entry condition, a practical path, and an exit condition. The exit condition tells you what the work has established. It does not claim more than that.

## Starting a new system

**Use this when:** You have a desired result but no established implementation.

1. Identify the users or operators, their important jobs, constraints, and success scenarios. Write down unresolved assumptions.
2. Describe what is inside the system boundary and what is outside it. Choose the simplest architecture that fits the real constraints, and record meaningful trade-offs.
3. Pick a thin end-to-end slice that produces an observable result. Define its boundary and acceptance checks.
4. Build and verify that slice. If a dependency is unavailable, use a substitute only when its limitation is recorded.
5. Explain the flow and failure behavior. Use what you learned to shape the next slice and update the system map.

**Done when:** The agreed slice meets its criteria and deferred capabilities are visible. One working slice does not prove that every planned feature works.

**Watch for:** Designing a large system and a large document hierarchy before testing an important assumption.

## Understanding an existing system

**Use this when:** You need to understand a codebase or prepare a change.

1. Read the project instructions, build and run entry points, architecture notes, tests, and relevant operational material.
2. Follow one representative behavior from input through its components and dependencies to its output or side effect.
3. Separate directly observed facts, interpretations supported by source, and unknowns. Run useful non-mutating checks when possible.
4. Map the existing layout and find the strongest available verification for the selected behavior.
5. Report gaps and a bounded next action. If implementation is requested, continue with the matching change workflow.

**Done when:** The selected boundary is mapped with evidence and explicit unknowns. Discovery-only work ends with findings; it does not implement proposed repairs.

**Watch for:** Moving files to fit EEM before understanding the project's own conventions and dependencies.

## Changing a feature or behavior

**Use this when:** You have an agreed capability or need to change existing behavior.

1. Describe current and expected behavior with concrete examples. Identify compatibility requirements and non-goals.
2. Follow the affected producers, consumers, storage, and external interfaces. Choose the failure cases that matter.
3. Define acceptance criteria before coding. Record a decision when a meaningful choice needs to be understood later.
4. Implement a bounded slice using the project's conventions.
5. Verify the new behavior and affected existing behavior. Recheck linked evidence and update the explanation.

**Done when:** The change meets its criteria, required human understanding is checked, and any release action has its own status.

**Watch for:** Testing only the new happy path while breaking an existing caller's contract.

## Diagnosing and repairing a bug

**Use this when:** Observed behavior differs from a valid expectation.

1. Record the symptom, expected behavior, environment, and smallest available reproduction. Confirm the source of the expectation.
2. Follow the failing path. Separate the immediate mechanism from a possible upstream or wider cause when the evidence allows it.
3. For diagnosis-only requests, explain the cause, evidence, uncertainty, and proposed repair. Stop before implementation.
4. When repair is authorized, add or choose a check that detects the original defect where practical. Change the narrowest boundary that actually fixes the cause.
5. Verify the reproduction and relevant neighboring cases. If the defect cannot be reproduced, state the confidence level and what observation would confirm the repair.

**Done when:** The diagnosis supports a cause at the available confidence, or the authorized repair meets its criteria. Do not call a hypothesis a demonstrated root cause.

**Watch for:** Broad refactoring during the search, which can hide both causality and verification.

## Handling an incident

**Use this when:** An active operational problem needs restoration or containment.

1. Establish the observed impact and the authority to take operational actions. Preserve a short timeline and relevant evidence.
2. Choose an authorized stabilization action using current observations and recovery options. During active impact, postpone documentation that cannot help the decision.
3. Verify stabilization through affected-user or operational indicators. Keep service restoration separate from root-cause resolution.
4. Investigate the cause, contributing conditions, and missed detection when the system is stable enough.
5. Link follow-up fixes and monitoring improvements. State what remains uncertain.

**Done when:** Stabilization and investigation have separate results and owners. If the request covered only stabilization, hand off the investigation explicitly.

**Watch for:** Treating service recovery as proof that the suspected cause was correct.

## Refactoring a system

**Use this when:** You want to improve structure while keeping intended behavior.

1. State the maintenance or comprehension problem in concrete terms. Name the behavior and compatibility properties that must stay unchanged.
2. Inspect existing checks. Add characterization checks when uncertainty makes them useful. Mark known defects as defects instead of silently turning them into requirements.
3. Choose a bounded restructuring and a way to judge the claimed improvement, such as a clearer dependency path or clearer ownership.
4. Make the structural change while keeping behavior changes visible as separate work.
5. Verify preserved behavior and show how the new structure addresses the stated problem. Update navigation and decisions.

**Done when:** Preserved behavior is supported under the checked conditions and the improvement is demonstrated. Renaming files alone is not evidence of better maintainability.

**Watch for:** Treating fewer files or shorter code as proof that the system is easier to maintain.

## Migrating data or interfaces

**Use this when:** You are changing stored data, schemas, interfaces, deployment arrangements, or another stateful boundary.

1. Identify affected versions, data, consumers, sequencing, and compatibility needs. Decide whether the operation can be reversed or safely repeated.
2. Define success and interruption behavior, including how the resulting state will be checked.
3. Plan recovery for the level of impact. If rollback is impossible, state that clearly and identify the authorized decision needed before the irreversible action.
4. Rehearse against a permitted representative environment or sample. Check constraints, counts or other relevant invariants, and mixed-version behavior when it matters.
5. Execute the real migration only when authorized. Observe the result, retain evidence, and report the actual recovery posture.

**Done when:** A prepared migration can be complete while execution is pending. An executed migration needs evidence about the resulting state, not just a successful command exit.

**Watch for:** Calling a backup a recovery plan without knowing whether it can actually be restored.

## Running a prototype or experiment

**Use this when:** You are testing an uncertain idea, design choice, or hypothesis.

1. State the question, alternatives, constraints, and the observation that would inform the next decision.
2. Choose the smallest useful experiment. Record assumptions, baselines, sampling, and limits before interpreting results.
3. Run it with enough version and environment information for the required reproducibility.
4. Separate observations from interpretation. Report negative and inconclusive results along with positive results.
5. Decide whether the evidence supports continuing, revising, stopping, or running a larger test. Do not quietly promote prototype code to a production component.

**Done when:** The agreed question has been addressed, even if the approach failed. Production readiness remains unassessed unless it was explicitly part of the experiment.

**Watch for:** Changing the success threshold after seeing the result and reporting the new threshold as if it had been planned from the start.

## Add domain-specific checks when needed

These prompts help you choose relevant checks. They are not complete domain standards.

| Domain | Pay attention to |
|---|---|
| Web, mobile, and UI | Interaction and error states, accessibility where required, devices or viewports covered, network behavior, client/server contract |
| Games | Player-visible behavior, deterministic versus variable behavior, state transitions, performance conditions, engine and asset versions |
| Data pipelines | Source provenance, data grain, schema, freshness, duplicate and missing data behavior, reruns, and partial failures |
| AI and ML | Dataset and model versions, evaluation independence, leakage risks, representative conditions, uncertainty, and fallback behavior |
| Embedded and IoT | Units, calibration, physical limits, timing, device and firmware versions, disconnect and power-loss behavior, physical validation |
| Libraries and APIs | Public compatibility, error meaning, supported versions, affected callers, deprecation, and migration behavior |

A model benchmark does not establish end-to-end hardware reliability. A UI screenshot does not establish accessibility. Always state the exact claim that an observation supports.
