# EEM workflows

Use the shared rules in [method.md](method.md). Choose the mode from the requested outcome. Combine modes only when the work needs it; a migration can include a feature change, and an incident can lead to a later bug fix.

## Greenfield system

**Entry:** A desired outcome without an established implementation.

1. Identify users or operators, their important jobs, constraints, and success scenarios. Record unresolved product assumptions.
2. Describe the system boundary and external dependencies. Select the simplest architecture that addresses the actual constraints; record significant trade-offs.
3. Select a thin end-to-end capability that produces an observable result. Define its contracts and acceptance checks.
4. Implement and verify that slice, using substitutes for unavailable dependencies only with the limitation recorded.
5. Explain the flow and failure behavior. Use findings to revise the next slice and the system map.

**Exit:** The agreed slice meets its criteria; deferred capabilities are visible. A working slice is not evidence that every planned feature works.

**Common mistake:** Designing a large hierarchy of subsystems and documents before testing any important assumption.

## Existing-system discovery

**Entry:** A request to understand an existing codebase or prepare a change.

1. Inspect project instructions, build/run entry points, architecture notes, tests, and relevant operational material.
2. Follow one representative behavior from its input through components and dependencies to its output or side effect.
3. Separate directly observed facts, source-supported interpretations, and unknowns. Run relevant non-mutating checks where feasible.
4. Map the existing layout and identify the strongest available verification for the selected behavior.
5. Report gaps and a bounded next action. If implementation is requested, continue using the applicable change workflow.

**Exit:** The selected boundary is mapped with evidence and explicit unknowns. Discovery-only work ends with findings, without implementing proposed repairs.

**Common mistake:** Moving source files to match EEM before understanding their conventions and dependencies.

## Feature or behavior change

**Entry:** An agreed capability or change to existing behavior.

1. Establish current and expected behavior with concrete examples. Identify compatibility requirements and non-goals.
2. Trace affected producers, consumers, storage, and external interfaces. Select the relevant failure cases.
3. Define acceptance criteria before coding. Record a decision only if a meaningful choice needs future explanation.
4. Implement a bounded slice using existing conventions.
5. Verify new behavior and affected existing behavior. Reassess linked evidence and update explanations.

**Exit:** The change meets its acceptance criteria, required understanding is checked, and any release action has its own explicit status.

**Common mistake:** Testing only the new happy path while breaking an existing caller's contract.

## Bug diagnosis and repair

**Entry:** Observed behavior differs from an expectation.

1. Record the symptom, expected behavior, environment, and smallest available reproduction. Confirm that the expectation has a valid source.
2. Trace the failing path. Distinguish the immediate mechanism from an upstream or systemic cause where evidence permits.
3. For diagnosis-only requests, explain the cause, supporting evidence, uncertainty, and proposed repair. Stop before implementation.
4. When repair is authorized, add or select a check that detects the original defect, where practical. Change the narrowest responsible boundary that adequately resolves the cause.
5. Verify the reproduction and relevant neighboring scenarios. If the defect cannot be reproduced, qualify confidence and state what observation would confirm the fix.

**Exit:** Diagnosis supports a cause at the available confidence, or the authorized repair meets its criteria. Do not label a hypothesis as a demonstrated root cause.

**Common mistake:** Broad refactoring while searching for a bug, obscuring both causality and verification.

## Incident

**Entry:** An active operational problem needing restoration or containment.

1. Establish the observed impact and authority to take operational actions. Preserve a minimal timeline and relevant evidence.
2. Choose an authorized stabilization action based on current observations and recovery options. During active impact, defer documentation that does not aid the decision.
3. Verify stabilization using the affected user or operational indicators. Distinguish service restoration from root-cause resolution.
4. Investigate the cause, contributing conditions, and missed detection when the system is stable enough.
5. Link follow-up fixes, monitoring improvements, and a concise explanation of what remains uncertain.

**Exit:** Stabilization and investigation have separate results and owners. If the request covers only stabilization, hand off the investigation explicitly.

**Common mistake:** Assuming service recovery proves the suspected cause was correct.

## Refactor

**Entry:** A structural improvement with intended behavior preserved.

1. State the concrete maintenance or comprehension problem. Name the behavior and compatibility properties that must remain unchanged.
2. Inspect existing checks and add characterization where uncertainty warrants it. Characterization records current behavior; flag known defects rather than silently making them requirements.
3. Choose a bounded restructuring and a way to judge the claimed improvement, such as a simpler dependency path or clearer ownership.
4. Make the change while keeping behavior changes separately visible.
5. Verify preservation and show how the structural change addresses the stated problem. Update affected navigation and decisions.

**Exit:** Preserved behavior is supported under the checked conditions, and the improvement is demonstrated rather than asserted from renamed files.

**Common mistake:** Treating fewer files or shorter code as sufficient evidence of improved maintainability.

## Migration

**Entry:** A change to stored data, schemas, interfaces, deployment arrangements, or another stateful boundary.

1. Identify affected versions, data, consumers, sequencing, and compatibility needs. Determine whether operations can be reversed or safely repeated.
2. Define success and interruption behavior, including validation of the resulting state.
3. Establish recovery arrangements appropriate to the impact. When rollback is impossible, make the recovery limitation explicit and identify the authorized decision needed before the irreversible action.
4. Rehearse against a representative permitted environment or sample. Verify constraints, counts or other relevant invariants, and mixed-version behavior where applicable.
5. Execute the actual migration only when authorized. Observe the result, retain evidence, and report the actual recovery posture.

**Exit:** A prepared migration may be implementation-complete while execution is pending. An executed migration requires evidence about the resulting state, not merely a successful command exit.

**Common mistake:** Calling a backup a recovery plan without knowing whether it is usable.

## Prototype or experiment

**Entry:** An uncertain feasibility question, design choice, or hypothesis.

1. State the question, alternatives, constraints, and what observation would inform the next decision.
2. Choose the smallest useful experiment. Record assumptions, relevant baselines, sampling, and limits before interpreting results.
3. Run it with enough version and environment information for the required reproducibility.
4. Separate observations from interpretation. Report negative and inconclusive findings along with positive findings.
5. Decide whether the evidence supports continuation, revision, stopping, or a larger test. Do not silently promote prototype code into a production component.

**Exit:** The investigation question is addressed to the agreed scope, even if the desired approach failed. Production readiness remains unassessed unless it was explicitly included.

**Common mistake:** Redefining the success threshold after seeing results and reporting the revised threshold as if it were original.

## Domain adaptations

Use these additions only when their claims are relevant. They are prompts for engineering judgment, not comprehensive domain standards.

| Domain | Additional attention |
|---|---|
| Web/mobile/UI | Interaction and error states, accessibility where required, devices or viewports covered, network behavior, client/server contract |
| Games | Player-visible behavior, deterministic versus variable behavior, state transitions, performance conditions, engine and asset versions |
| Data pipelines | Source provenance, grain, schema, freshness, duplicate/missing data behavior, rerun and partial-failure semantics |
| AI/ML | Dataset and model versions, evaluation independence, leakage risks, representative conditions, uncertainty, fallback behavior |
| Embedded/IoT | Units, calibration, physical limits, timing, device/firmware versions, disconnect and power-loss behavior, physical validation |
| Libraries/APIs | Public compatibility, error semantics, supported versions, callers affected, deprecation or migration behavior |

A model benchmark does not establish a hardware system's end-to-end reliability. A UI screenshot does not establish accessibility. Specify the exact claim each observation supports.
