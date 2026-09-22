# EEM v0.1 — Method specification

EEM is a way to keep a project understandable from the first question through the finished change. It connects the intended result, the implementation, the checks that were run, and the understanding needed to maintain the system later.

**Status:** operational draft for trial. Real project outcomes have not yet established how effective the method is.

## How to use this guide

Start with the smallest piece of work that matters. Choose a workflow and a level of detail that fit the risk. Reuse the project's existing issue, task, pull request, or notes when they already contain the needed information.

EEM can be used with software, data, models, hardware interfaces, and combinations of them. It does not prescribe a language, framework, architecture, folder layout, or development tool. It also does not by itself establish security, regulatory compliance, scientific validity, or production readiness.

## 1. The principles

1. **A claim needs support.** An intention, an implementation, and an observed result are three different things.
2. **People need to understand what they own.** An assistant can write a helpful explanation, but that does not prove that the responsible person understands the system.
3. **Important boundaries should be visible.** Describe the responsibility, inputs, outputs, dependencies, side effects, and relevant failures.
4. **Use more rigor when the stakes or uncertainty are higher.** Code size and document count are poor substitutes for risk assessment.
5. **Every artifact should earn its place.** Keep a document or step when it helps someone decide, check, understand, or maintain the work.
6. **Trace meaningful relationships.** Connect requirements, decisions, code, checks, and results without forcing every line into a tracking table.
7. **Keep the map current.** When behavior or assumptions change, review the records and evidence that depend on them.

## 2. A few terms

| Term | Plain meaning |
|---|---|
| Outcome | The useful result the work is meant to produce |
| Requirement | An expected behavior or constraint, with a source or reason |
| Acceptance criterion | An observable condition used to judge one result |
| Definition of Done | Shared completion conditions for a project or type of work |
| Contract | What a boundary needs, promises, and does when something fails |
| Feature | A recognizable system capability; it may use several components |
| Work Record | A maintained record for a bounded change, investigation, or experiment |
| Decision record | The context, choice, alternatives, and consequences of a significant decision |
| Evidence | An inspectable observation or result that supports a particular claim under stated conditions |
| Traceability | Navigable links between the intent, decisions, implementation, checks, and results |

EEM explains engineering behavior. It does not claim to explain the internal reasoning of an ML model.

## 3. Keep three kinds of information separate

| Kind of information | Examples | What it tells us |
|---|---|---|
| Intent and design | Requirements, contracts, design notes, decisions | What should happen and why |
| Implementation | Code, configuration, schemas, models, hardware arrangements | What has been built |
| Verification evidence | Test runs, measurements, experiments, review findings | What was observed or assessed |

A test definition describes a check. A test execution produces a result. A design review can support a claim about the design, but it cannot demonstrate runtime behavior on its own.

Traceability connects these records. One requirement may map to several components and checks. One component may support several requirements. A failing check should lead back to the behavior it protects.

Use stable issue IDs, symbols, paths, and revision IDs where they exist. A link to a moving file helps navigation but does not identify the exact version that was tested. Store that version in the evidence record.

Keep each fact in one clear, authoritative place and link to it from summaries. A traceability table is optional when the project already has a tool that exposes the same relationships. Diagrams may omit detail, but they must not contradict the behavior they claim to show.

## 4. Roles and authority

A small project may have one person doing several jobs:

- **Outcome owner:** resolves intent, scope, and acceptance trade-offs.
- **Implementer:** makes the authorized change and records relevant results.
- **Verifier or reviewer:** checks the result against the criteria.
- **Explanation owner:** needs to understand the boundary well enough to maintain it.
- **Release operator:** performs release actions when they are authorized and needed.

Record names or roles only when ownership matters. Do not invent an approver for routine work.

AI may inspect, draft, implement, test, and explain within its authorization. It must separate recommendations from accepted decisions and observations from assumptions. Instructions for the AI describe how it works; product contracts describe what the system does. Permission to explore a design does not permit changing agreed behavior.

Independent review checks the original criteria and raw evidence without relying only on the implementer's story. Another agent can provide a separate review when authorized, but it is not a substitute for a qualified human or specialist when one is needed. Label a self-review as a self-review.

## 5. Choose the right level of rigor

Choose a level at the start and revisit it if new information changes the impact or uncertainty. Write the reason in one sentence. These are working categories, not numerical risk scores.

| Level | Typical situation | Minimum useful treatment |
|---|---|---|
| Lightweight | Local, reversible change with familiar behavior and limited consequences | Short outcome and boundary note, acceptance criteria, an appropriate check, and code/result links |
| Standard | Several components, a changed interface, user-visible behavior, or meaningful uncertainty | Work Record, relevant contract and failure cases, decision rationale, acceptance checks, and affected regression checks |
| Heightened | Possible data loss, access-control failure, irreversible migration, physical consequences, or difficult recovery | Standard treatment plus failure analysis, specialist or independent review where needed, representative verification, and recovery provisions |

A one-line change can still need heightened treatment if its consequences are serious. A reversible UI text change usually does not need the same treatment as a payment calculation or destructive migration.

For heightened work, name the specific review and evidence required. If they are unavailable, show the completion or release condition as pending. The label does not authorize extra services, external mutations, or delegation by itself.

The human explanation depth depends on who must operate or maintain the result. A learning project may need a walkthrough for a small change. A routine text fix may record the check as not required.

## 6. The work loop

### Frame the work

Identify the outcome, current state, relevant requirements, scope, uncertainty, workflow mode, and rigor. With an existing system, inspect before proposing structural changes. Separate observed behavior from guesses based on names or comments.

### Plan the check

Define acceptance criteria and how each one can be assessed. Record important boundaries and decisions. Add non-goals when they prevent likely scope drift. Keep criteria independent of the proposed implementation where possible.

### Implement or investigate

Make a bounded change or collect the observations needed to answer the question. Keep findings in the Work Record when they affect a decision. Reuse project conventions. If the findings undermine the plan, return to framing or design and record the change in direction.

### Verify the result

Assess the material criteria and relevant neighboring behavior. A passing local check supports the conditions it covers; it does not automatically prove integration, production behavior, or release readiness.

### Explain the result

Provide the needed system map, decision rationale, interpretation of evidence, or walkthrough. Perform the human check when it is required and possible. Technical work can continue while that check is pending.

### Close or hand off

Update the records affected by the change. Report separate statuses and name unresolved conditions and their owners. Treat release as its own authorized project action.

The loop repeats. Do not leave all documentation and traceability until the end, and do not demand that every artifact be perfect before implementation teaches you something new.

## 7. Verification and evidence

### Choose a check that matches the claim

- **Calculation:** examples, boundary cases, properties, or comparison with an independent reference.
- **Component interaction:** integration checks, including relevant timeout and failure behavior.
- **User workflow:** acceptance or UI checks for the stated scenario.
- **Hardware interaction:** simulation and physical observation when the claim is physical.
- **Model or data claim:** suitable data, provenance, evaluation design, and stated limitations.
- **Non-executable change:** inspection, rendering, or link checks when they address the actual risk.

These are options, not a checklist to complete every time. Do not copy the same formula into code and a test and call that independent confirmation. Do not add a test just to satisfy a template.

### Record the evidence

For each material result, record the claim or acceptance criterion, method, result, artifact location, time, and conditions that affect interpretation. Include the code revision or change snapshot, environment, configuration, and data or model versions when they matter. Preserve failures as well as successes when they change the conclusion.

An evidence ID may point to a CI run, test report, measurement sheet, screenshot, review, or recorded manual check. Do not copy sensitive raw data into documentation when a controlled reference is enough.

Use separate fields for:

- **Result:** passed, failed, not run, or inconclusive.
- **Applicability:** current, needs reassessment, or superseded.

An old passing result stays historically passed even when a later change means it needs reassessment.

### When evidence changes or conflicts

When behavior, configuration, dependencies, data, models, or assumptions change, identify the claims that may be affected. Rerun or replace the relevant checks. Do not discard unrelated evidence automatically.

If sources disagree, record the disagreement, versions, and scope of each observation. Investigate before presenting one conclusion. Do not choose only the result that supports completion.

### Correct a failure in a bounded way

Form a specific explanation, make a scoped correction, and rerun the relevant checks. Broaden verification when the failure reveals wider impact. When repeated attempts produce no new information, stop retrying, preserve the evidence, and identify the missing capability or decision.

## 8. Check human understanding

For important work, choose the explanation dimensions that matter:

| Dimension | The person can demonstrate that they can… |
|---|---|
| Locate | Find the entry point and important components |
| Contract | Describe inputs, outputs, limits, side effects, and failures |
| Rationale | Explain a significant design choice and its trade-off |
| Evidence | Say what a result supports and what it leaves unknown |
| Diagnose | Identify a sensible first place to look when it fails |

Use a representative scenario and ask the responsible person to explain it in their own words, using the repository and documents when needed. For example: “The external service times out. What should the user see, where is that behavior implemented, and what check supports it?”

Record who participated, the boundary and scenario, the dimensions checked, and any gaps. Use **completed**, **pending**, or **not required**, with a reason. Completion means the selected scope was demonstrated; it does not mean universal mastery of the whole system.

If a gap appears, improve the explanation or design, practice the scenario, and revisit the gap. AI can prepare questions and feedback. It cannot mark a person's understanding complete just because it supplied a correct answer.

## 9. Completion and exceptions

Keep these statuses separate:

| Area | Suggested states |
|---|---|
| Implementation or investigation | Not started, in progress, complete |
| Verification | Pending, passed, failed, inconclusive |
| Required explanation | Pending, completed, not required |
| Work disposition | Open, closed, closed with exception |
| Release, if relevant | Not requested, pending, released, rolled back |

Close the work when its acceptance conditions are supported, required explanation checks are complete, affected records are current, and remaining limits are stated.

An investigation can be complete with a supported negative or inconclusive result when that answers its investigation question. That does not mean the underlying product requirement passed.

A failed or unchecked material criterion stays visible. Do not quietly turn it into a pass. If the outcome owner accepts an exception within their authority, record the unmet condition, evidence, consequence, compensating measure if relevant, owner, and review trigger or expiry. Use **closed with exception**. The assistant cannot grant itself an exception.

Task completion and release readiness are separate. A completed prototype may still be unsuitable for production. A released system may carry a documented exception.

## 10. Keep the method healthy

Start with a short Work Record and links for one capability. Add detail when a real change creates a need. Avoid repository-wide renaming, blanket file limits, and mandatory feature folders.

When an interface or assumption changes, inspect linked consumers, checks, explanations, and decisions. Update affected records in the same change when practical. Mark an old decision as superseded and link to its replacement rather than rewriting history.

During a handoff, include the relevant revision, current status, strongest evidence, known limits, and the next owner's action. Keep a durable record for work that spans sessions.

Use the [trial plan](trial-plan.md) to assess EEM. Change the method in response to observed problems and test whether the change helps. Record material method revisions and recheck earlier successful scenarios for regressions. v0.1 does not claim novelty for established engineering practices or verified fidelity to external methods mentioned in the original discussion.
