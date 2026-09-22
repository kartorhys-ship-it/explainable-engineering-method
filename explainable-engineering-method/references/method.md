# EEM v0.1 — Method specification

Status: operational draft for trial. The method's usefulness has not yet been established through project outcomes.

## Contents

1. Purpose and applicability
2. Principles and terminology
3. Working structure and traceability
4. Roles and authority
5. Rigor selection
6. Lifecycle
7. Verification and evidence
8. Human explanation
9. Completion and exceptions
10. Maintenance and adoption

## 1. Purpose and applicability

EEM helps people build, change, investigate, and maintain systems they can explain. It addresses both system behavior and the relationship between a claim and the evidence supporting it.

For important work, a responsible person should be able to explain why it exists, where it lives, what its boundaries are, why significant decisions were made, what has been verified, and how failure would be investigated.

The method can govern software, data, models, hardware interfaces, and combinations of these. Domain suitability must be tested. EEM does not prescribe a programming language, architecture, directory tree, or development tool. It does not by itself establish security, regulatory compliance, scientific validity, or operational readiness.

General use begins with a small project trial. Do not retrofit an entire repository merely to make it resemble a template.

## 2. Principles and terminology

### Core principles

1. Claims require proportionate evidence. A stated intention, an implementation, and an observed result are different things.
2. Human understanding is checked through human performance. An explanation produced by an assistant is supporting material.
3. Boundaries are explicit where ambiguity matters: responsibilities, inputs, outputs, dependencies, side effects, and failures.
4. Rigor follows impact, uncertainty, and recoverability. Lines of code and file counts do not determine risk.
5. Complexity must serve a concrete need. Every artifact should help someone decide, verify, understand, or maintain.
6. Trace meaningful relationships. Do not trace every line or require one-to-one mappings.
7. Preserve alignment during change. Update affected claims and reconsider evidence whose assumptions no longer hold.

### Terms

| Term | Meaning |
|---|---|
| Outcome | The useful result the work aims to achieve |
| Requirement | An expected behavior or constraint with a source or rationale |
| Acceptance criterion | An observable condition used to judge a particular result |
| Definition of Done | Shared completion conditions for this project or class of work, in addition to task-specific criteria |
| Contract | What a boundary promises and requires, including relevant failure behavior |
| Feature | A recognizable system capability; it may span several components |
| Work Record | The maintained account of a bounded change, investigation, or experiment |
| Decision record | The context, choice, alternatives, and consequences of a significant decision |
| Evidence | An inspectable observation or result supporting a specified claim under stated conditions |
| Traceability | Navigable relationships between intent, decisions, implementation, checks, and results |

Explainability concerns the engineering system. It does not imply that an ML model's internal reasoning has been explained.

## 3. Working structure and traceability

Maintain three distinguishable kinds of information:

| Kind | Examples | Establishes |
|---|---|---|
| Intent and design | Requirements, contracts, design notes, decisions | What is expected and why |
| Implementation | Code, configuration, schemas, models, hardware arrangements | What has been constructed |
| Verification evidence | Test runs, measurements, experiments, review findings | What was observed or assessed |

A test definition describes a check; a test execution supplies a result. A design review may support a design-quality claim but cannot demonstrate runtime behavior by itself.

Traceability joins these records. For example, a requirement can link to two features, a shared component, several acceptance checks, and the results from a particular revision. Conversely, a failing test should lead back to the behavior it protects.

Use stable issue identifiers, symbols, repository paths, and revision identifiers where available. A link to a moving file can help navigation but cannot identify the exact version previously tested. Preserve that version in the evidence record.

Keep each fact in a clear authoritative location. Link to it from other views. A traceability table is optional if existing tools already expose the necessary relationships. Diagrams represent architecture views and may omit details; they must not contradict the behavior they claim to describe.

## 4. Roles and authority

A small project may have one person holding several roles:

- Outcome owner: resolves product intent, scope, and acceptance trade-offs.
- Implementer: makes the authorized change and records relevant results.
- Verifier or reviewer: assesses the result against the criteria.
- Explanation owner: needs to understand the relevant system boundary.
- Release operator: performs release when authorized and applicable.

Record names or roles only where ownership matters. Do not invent an approver for a routine task.

AI may inspect, draft, implement, test, and explain within its authorization. It must distinguish recommendations from accepted decisions and observations from assumptions. AI operating instructions govern how the assistant works; system contracts govern what the product does. A deterministic product rule does not eliminate implementation choices, and permission to explore designs does not permit altering agreed behavior.

Independent review means assessment against original criteria and raw evidence without depending solely on the implementer's account. Another agent can provide a separate review pass when authorized, but it is not a substitute for a qualified human or specialist where one is needed. A self-review should be labeled as such.

## 5. Rigor selection

Select a level at the start and revisit it when discoveries change the impact or uncertainty. State the reason in one sentence. These are working categories, not numerical risk scores.

| Level | Typical conditions | Minimum useful treatment |
|---|---|---|
| Lightweight | Local, readily reversible change; well-understood behavior; limited consequences | Short outcome and boundary note, acceptance criteria, appropriate check, code/result links |
| Standard | Several components, changed interface, user-visible behavior, or meaningful uncertainty | Work Record, relevant contract and failure cases, decision rationale, acceptance verification and affected regression checks |
| Heightened | Potential material data loss, access-control failure, irreversible migration, consequential physical effects, or difficult recovery | Standard treatment plus explicit failure analysis, relevant specialist or independent review, representative verification, and recovery provisions where applicable |

One consequential risk can warrant heightened treatment even for a one-line change. A reversible UI text fix does not need the same treatment as a payment calculation or destructive migration.

For heightened work, identify the specific review and evidence needed. If unavailable, show the completion or release condition as pending. The classification does not itself authorize extra services, external mutations, or delegation.

Human explanation depth depends on who needs to operate or maintain the result. A learning project may require a walkthrough for a small change. A routine text fix may record the check as not required.

## 6. Lifecycle

### Frame

Identify the outcome, current state, relevant requirements, scope, uncertainty, working mode, and rigor. For existing systems, inspect before proposing structural changes. Distinguish observed behavior from behavior inferred from names or comments.

### Plan

Define acceptance criteria and how each can be assessed. State important boundaries and decisions. Specify non-goals when they prevent likely scope drift. Keep criteria independent of the proposed implementation where possible.

### Implement or investigate

Make a bounded change or collect relevant observations. Keep ongoing findings in the Work Record when they affect a decision. Reuse established conventions. If findings undermine the plan, return to framing or design and record the material change.

### Verify

Assess the material criteria and relevant neighboring behavior. A passing local check supports its covered conditions; it does not automatically establish integration, production behavior, or release readiness.

### Explain

Provide the needed system map, rationale, evidence interpretation, or walkthrough. Perform the human check when required and possible. Finish independent technical work if that check is pending.

### Close or hand off

Update affected records and report distinct statuses. Identify unresolved conditions and their owners. Release only as part of the actual authorization and project process.

This lifecycle repeats. Do not defer all documentation and traceability until the end, and do not require every artifact to be finalized before learning through implementation.

## 7. Verification and evidence

### Choose the check from the claim

- Pure calculation: examples, boundary cases, properties, or comparison to an independent reference.
- Component interaction: integration checks, including relevant timeout and failure behavior.
- User workflow: acceptance or UI checks of the stated scenario.
- Hardware interaction: simulation and physical observation where the physical claim requires it.
- Model or data claim: suitable datasets, provenance, evaluation design, and stated limitations.
- Non-executable change: inspection, rendering, or link checks where these address the actual risk.

These are options. Avoid duplicating a formula in a test and treating agreement as independent confirmation. Avoid introducing tests solely to satisfy a template.

### Evidence record

Record the claim or acceptance criterion, method, result, artifact location, time, and conditions that materially affect interpretation. Include the code revision or change snapshot, environment, configuration, and data/model identifiers when relevant. Preserve failures as well as successes when they affect the conclusion.

An evidence identifier may reference a CI run, test report, measurement sheet, screenshot, review, or recorded manual check. Do not copy sensitive raw data into documentation when a controlled reference suffices.

Use separate fields:

- Result: passed, failed, not run, or inconclusive.
- Applicability: current, needs reassessment, or superseded.

An old passing result remains historically passed even when it needs reassessment for new code.

### Changed or conflicting evidence

When behavior, configuration, dependencies, datasets, or assumptions change, identify affected claims and check whether their prior evidence still applies. Re-run or replace the relevant checks; do not invalidate unrelated evidence automatically.

If sources conflict, record the disagreement, versions, and scope of the observations. Reproduce or investigate it before presenting a unified conclusion. Do not select only the result that supports completion.

### Bounded correction

For a failure, form a specific explanation, make a scoped correction, and rerun the relevant checks. Broaden verification when the failure reveals wider impact. When attempts repeat without new information, stop retrying, preserve evidence, and identify the missing capability or decision.

## 8. Human explanation

Assess relevant dimensions, without treating them as a validated score or a mandatory progression:

| Dimension | A person can demonstrate |
|---|---|
| Locate | Find the entry point and the important components |
| Contract | Describe inputs, outputs, limits, side effects, and failures |
| Rationale | Explain a significant design choice and its trade-off |
| Evidence | Explain what a result supports and what it leaves unknown |
| Diagnose | Identify where to look first for a plausible failure |

For a required check, choose a representative scenario and ask the responsible person to explain it in their own words, using the repository and documents if needed. For example: "The external service times out. What should the user see, where is that behavior implemented, and what check supports it?"

Record who participated, which boundary and scenario were checked, the dimensions addressed, and any gaps. Use completed, pending, or not required with a reason. Completion means the selected scope was demonstrated, not universal mastery of the system.

If a gap appears, improve the explanation or design, practice the relevant scenario, and revisit the gap. AI may prepare questions and feedback. It cannot mark the person's understanding complete merely because it supplied a correct answer itself.

## 9. Completion and exceptions

Keep separate statuses:

| Area | Suggested states |
|---|---|
| Implementation or investigation | Not started, in progress, complete |
| Verification | Pending, passed, failed, inconclusive |
| Required explanation | Pending, completed, not required |
| Work disposition | Open, closed, closed with exception |
| Release, if relevant | Not requested, pending, released, rolled back |

The work can close when its agreed acceptance conditions are supported, required explanation checks are complete, affected records are current, and remaining limitations are stated. An investigation may be complete with a well-supported negative or inconclusive finding if that satisfies its investigation objective; this is distinct from claiming the underlying product requirement passed.

A material criterion that failed or was not checked remains visible. Do not silently change it into a pass. If the outcome owner accepts an exception within their authority, record the unmet condition, available evidence, consequence, compensating measure if relevant, owner, and review trigger or expiry. Use closed with exception. The assistant cannot grant itself an exception to a user's requirement.

Release readiness and task completion are related but separate. A completed prototype need not be ready for production. A released system may have a documented exception rather than all checks passed.

## 10. Maintenance and adoption

Start with a short Work Record and links for one capability. Extend coverage when a change creates a practical need. Avoid repository-wide renaming, blanket file limits, or mandatory feature folders.

When an interface or assumption changes, inspect linked consumers, checks, explanations, and decisions. Update the affected records in the same change where practical. A historical decision should be marked superseded and linked to its replacement rather than rewritten to suggest it was always different.

During handoff, include the relevant revision, current status, strongest supporting evidence, known limitations, and the next owner action. Keep a durable record for work that will span sessions.

Evaluate EEM through the [trial plan](trial-plan.md). Change its rules in response to observed problems and test whether the revision helps. Record material method changes and recheck prior successful scenarios for regressions. v0.1 does not claim novelty for established engineering practices or verified fidelity to external methodologies mentioned in the original discussion.
