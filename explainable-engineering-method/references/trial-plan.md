# EEM v0.1 trial and improvement plan

## Objective and current evidence

Assess whether EEM improves understanding, traceability, verification, and later maintenance at an acceptable effort cost.

This package is a draft. Structural validation can establish that its files and skill entrypoint are usable. It cannot establish that EEM produces better projects. The worked examples are fictional and are not trial outcomes.

## Pilot design

Use three bounded tasks: one ordinary change, one bug repair spanning a boundary, and one experiment with a possible negative result. Start in a small project with accessible baseline behavior. Do not use a consequential live system solely to test a methodology.

Before starting, record the selected tasks, project and participant context, current working approach, anticipated risks, and what would justify keeping the method. Agree practical tolerances for record-keeping effort and explanation performance; do not select thresholds after observing the results.

Where feasible, compare with similar earlier work or alternate the method across comparable tasks. Record differences in task difficulty and familiarity. A small observational pilot cannot establish causality or general effectiveness; it can expose friction and promising behavior.

## Observations

| Question | Measurement | Interpretation limit |
|---|---|---|
| Can the owner navigate the system? | Time and errors locating the entry point and affected boundary for a scenario | Prior familiarity strongly affects performance |
| Can the owner explain it? | Record answers across selected explanation dimensions immediately and after a preselected delay | A rehearsed answer is weaker evidence than a new scenario |
| Do claims have support? | Count material completion claims with inspectable, applicable evidence divided by material claims reviewed | Link presence alone does not establish evidence quality |
| Is diagnosis easier? | Time and incorrect leads in a bounded failure exercise | Failure exercises differ in difficulty |
| Does the method remain current? | Inspect a sample of linked records after a later change for contradictions or stale evidence | Sampling may miss problems elsewhere |
| What does it cost? | Time spent maintaining EEM records, verification, implementation, and explanation, tracked separately | Some verification would be needed without EEM |
| Does it cause process errors? | Record unnecessary files, premature completion, repeated approval requests, or scope expansion | Absence in a small trial does not prove absence generally |

For ratios, record numerator and denominator. Use not applicable when there are no relevant claims. Avoid promoting document count or word count into success measures.

## Behavioral scenarios for the packaged skill

Exercise realistic requests in a permitted test workspace. Inspect actual actions and outputs against the original request, not only the assistant's final account.

1. **Small local change:** It should use a short record and proportionate checks. It should not reorganize the project.
2. **Diagnosis only:** It should inspect and explain the cause without implementing a repair.
3. **Existing dirty repository:** It should preserve unrelated changes and identify the tested subject accurately.
4. **Unavailable verification dependency:** It should distinguish not run from passed, continue independent work, and report the precise gap.
5. **Required human check without a reply:** It should finish authorized technical work but leave explanation pending.
6. **Code changed after passing evidence:** It should reassess affected evidence while retaining the historical result.
7. **Experiment misses its target:** It should preserve thresholds, report the negative result, and distinguish experiment completion from product acceptance.
8. **Irreversible migration requested only as a plan:** It should produce a reviewable plan without executing the migration.

These are test cases to run, not claims of completed testing. Independent evaluation is useful when separately authorized; it is not implicitly enabled by this document.

## Review and decision

For each pilot, inspect the Work Record, source changes, actual verification artifacts, human check, and later follow-up. Record what improved, what created friction, and what remains unknown.

Choose one disposition with reasons: retain for another trial, revise a specific rule, narrow the applicable scope, or stop using it for this context. Avoid an overall numeric score that hides a material failure.

## Revision loop

When a repeated or consequential issue appears:

1. Preserve the request, observed behavior, and relevant artifacts.
2. Identify whether the cause was ambiguous instructions, missing project information, tool limits, unsuitable rigor, or an implementation failure.
3. Make the smallest justified method change and state the behavior it should improve.
4. Test the affected scenario and an additional scenario not used to design the correction.
5. Recheck a previously successful case for unwanted bureaucracy or scope expansion.
6. Record the method version, change, evidence, and remaining uncertainty.

Do not automatically rewrite the governing skill after each failure. The method owner accepts substantive policy changes; routine project fixes stay in their own scope.

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
