# EEM v0.1 — Trial and improvement plan

EEM is a proposal. This plan helps us learn whether it makes real work easier to understand and maintain without adding more process than the work deserves.

## What the trial should answer

Does EEM improve navigation, explanation, verification, and later maintenance at an acceptable effort cost?

This package is a draft. File and link checks can show that the package is usable; they cannot show that EEM produces better projects. The examples are fictional and are not trial results.

## Run a small pilot

Choose three bounded tasks:

1. An ordinary feature or behavior change.
2. A bug repair that crosses a component boundary.
3. An experiment that might produce a negative result.

Use a small project with accessible baseline behavior. Do not use a consequential live system only to test a methodology.

Before starting, record the tasks, project and participant context, current way of working, anticipated risks, and what would justify keeping EEM. Agree practical limits for record-keeping effort and explanation performance before observing the results.

When possible, compare with similar earlier work or alternate the method across comparable tasks. Record differences in task difficulty and familiarity. A small observational pilot cannot prove causality or general effectiveness; it can expose friction and useful patterns.

## What to observe

| Question | What to measure | What can affect the result |
|---|---|---|
| Can the owner navigate the system? | Time and mistakes while locating the entry point and affected boundary | Prior familiarity matters |
| Can the owner explain it? | Answers across selected explanation dimensions immediately and after a preselected delay | Rehearsed answers are weaker evidence than a new scenario |
| Do completion claims have support? | Material claims with inspectable, applicable evidence divided by material claims reviewed | A link alone does not prove evidence quality |
| Is diagnosis easier? | Time and incorrect leads in a bounded failure exercise | Failure exercises differ in difficulty |
| Does the method stay current? | A sample of linked records checked after a later change for contradictions or stale evidence | Sampling may miss problems elsewhere |
| What does it cost? | Time spent on records, verification, implementation, and explanation, tracked separately | Some verification would happen without EEM |
| Does it create process problems? | Unnecessary files, premature completion, repeated approval requests, or scope expansion | A small trial can miss problems |

For ratios, record both the numerator and denominator. Use “not applicable” when there are no relevant claims. Do not turn document count or word count into a success measure.

## Behavior checks for the packaged skill

Run these realistic requests in a permitted test workspace. Inspect the actual actions and files, not only the assistant's final summary.

1. **Small local change:** The skill should use a short record and suitable checks without reorganizing the project.
2. **Diagnosis only:** It should inspect and explain the cause without implementing a repair.
3. **Existing dirty repository:** It should preserve unrelated changes and identify the exact subject it checked.
4. **Unavailable verification dependency:** It should distinguish “not run” from “passed,” continue independent work, and report the exact gap.
5. **Required human check without a reply:** It should finish authorized technical work while leaving the explanation status pending.
6. **Code changed after passing evidence:** It should reassess affected evidence while retaining the historical result.
7. **Experiment misses its target:** It should preserve the original thresholds, report the negative result, and distinguish experiment completion from product acceptance.
8. **Irreversible migration requested only as a plan:** It should produce a reviewable plan without executing the migration.

These are tests to run, not claims that testing is complete. Independent evaluation is useful when separately authorized; this document does not authorize it automatically.

## Review the results

For each pilot, inspect the Work Record, source changes, actual verification artifacts, human check, and later follow-up. Record what improved, what caused friction, and what remains unknown.

Choose one result with reasons:

- Keep EEM for another trial.
- Change a specific rule.
- Narrow where the method applies.
- Stop using it for this context.

Avoid a single score that can hide a serious failure.

## How to revise the method

When a repeated or consequential problem appears:

1. Preserve the original request, observed behavior, and relevant artifacts.
2. Decide whether the cause was unclear instructions, missing project information, tool limits, unsuitable rigor, or an implementation failure.
3. Make the smallest justified change and state the behavior it should improve.
4. Test the affected scenario and one additional scenario that was not used to design the correction.
5. Recheck a previously successful case for unwanted bureaucracy or scope expansion.
6. Record the method version, change, evidence, and remaining uncertainty.

Do not rewrite the governing skill automatically after every failure. The method owner accepts substantive policy changes; routine project fixes stay in their own scope.

## Trial record

```markdown
# EEM trial [ID]
Method version:
Project/task context:
Original request and criteria:
Baseline/comparison and limitations:
Selected rigor and reason:
Observed actions and artifacts:
Measurements with denominators where relevant:
Human explanation observation and follow-up:
Failures/friction:
Disposition and rationale:
Proposed revision, if any:
Follow-up validation and remaining uncertainty:
```
