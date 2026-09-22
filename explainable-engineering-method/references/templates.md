# EEM templates

These templates are starting points, not forms that every task must complete in full. Copy the smallest one that gives the work a useful record. An issue, task, pull request, notebook, or existing project document can carry the same information.

Text in `[square brackets]` is a field to fill in. It is not a request to create another file. Delete fields that do not apply.

## Lightweight Work Record

Use this for a small, local, and reversible change.

```markdown
# [ID or title]

Outcome: [useful result and reason]
Mode / rigor: [mode, level, one-sentence reason]
Scope and boundaries: [change, relevant input/output, exclusions]

Acceptance:
- [observable condition]

Implementation: [source links and relevant revision/snapshot]
Verification: [criterion -> check -> actual result/evidence]
Limitations: [remaining uncertainty, or none identified within the checked scope]
Explanation: [completed / pending / not required; reason and scope]
Status: [implementation; verification; work disposition; release if relevant]
Next action: [action and owner, or none]
```

## Extended Work Record

Use this when several components, a changed interface, meaningful uncertainty, or a higher-consequence failure makes the extra context useful.

```markdown
# [ID]: [title]

## Context
Outcome and source: [problem, user need, or investigation question]
Mode: [workflow]
Rigor: [level and reason]
Responsible people: [roles whose ownership matters]
Related requirements: [links]
Current behavior: [observed behavior and evidence]
Unknowns/assumptions: [what is inferred or unresolved]

## Scope and contracts
Included: [boundaries changed]
Non-goals: [likely misunderstandings to exclude]
Inputs/preconditions: [types, units, validity where relevant]
Outputs/postconditions: [results and promises]
Side effects/dependencies: [relevant relationships]
Failures: [trigger -> expected handling]
Compatibility: [consumers and preserved behavior]

## Approach
Design: [enough detail to understand the change]
Significant decisions: [links or short rationale]
Risks and recovery: [relevant consequences and responses]

## Acceptance and evidence
| Criterion | Check/method | Result | Evidence | Applicability |
|---|---|---|---|---|
| [observable condition] | [method] | [passed/failed/not run/inconclusive] | [link] | [current/needs reassessment/superseded] |

## Outcome
Implementation: [paths, symbols, revision]
Findings/limitations: [observations separate from interpretation]
Affected records updated: [links]
Human explanation: [person, scenario, dimensions, gaps, status]
Statuses: [implementation; verification; explanation; disposition; release]
Remaining actions: [action, owner, trigger]
Exceptions: [none or explicit record]
```

## Decision record

Use this for a choice that someone may need to understand or revisit later. Routine implementation details do not need decision records.

```markdown
# [Decision ID]: [choice]
Status: [proposed / accepted / superseded]
Context: [constraint or problem]
Options considered: [credible alternatives and relevant trade-offs]
Decision: [choice; decision owner when material]
Reason: [evidence and reasoning]
Consequences: [benefits, costs, limitations]
Revisit when: [assumption or trigger]
Related work/evidence: [links]
Supersedes / superseded by: [link if applicable]
```

## Evidence record

Use this to show exactly what a check supports. A test definition is the method; an execution of that test is the evidence.

```markdown
# [Evidence ID]
Claim/criterion: [exact statement assessed]
Method: [command, procedure, measurement, or review scope]
Observed result: [passed / failed / not run / inconclusive, with details]
Artifact: [report, run, screenshot, log, or recorded observation]
Recorded at/by: [time and actor]
Subject version: [revision or change snapshot]
Relevant conditions: [environment/configuration/data/model versions]
Limits: [what this does not establish]
Applicability: [current / needs reassessment / superseded]
Reassessment reason/replacement: [if applicable]
```

Omit irrelevant version fields. Keep any version that changes the meaning of the claim.

## Traceability view

Use this when a reader needs a visible path from a requirement or question to the code and its supporting check. Many-to-many relationships may need several rows.

```markdown
| Requirement or question | Work | Implementation boundary | Check | Evidence | Gap |
|---|---|---|---|---|---|
| [link] | [link] | [path/symbol/interface] | [link] | [versioned result] | [none or specific gap] |
```

Do not force one feature or one test to represent a wider requirement when the real relationship is broader.

## Human explanation record

Use this when the responsible person needs to demonstrate understanding of a boundary.

```markdown
Boundary: [capability being explained]
Responsible person: [actual participant]
Scenario: [normal flow, failure, or proposed change]
Dimensions selected: [locate / contract / rationale / evidence / diagnose]
Observed demonstration: [what the person explained or located]
Gaps and follow-up: [specific issue and action]
Status: [completed / pending / not required]
Reason if not required: [scope rationale]
```

An assistant-written explanation is preparation material. It does not replace this check when the check is required.

## Exception record

Use this when an outcome owner accepts a known gap within their authority.

```markdown
Unmet condition: [criterion or required check]
Evidence and consequence: [known facts and exposure]
Disposition: [what is being accepted despite the gap]
Accepted by: [authorized outcome owner; pending if not accepted]
Compensating measure: [if relevant]
Follow-up owner and review trigger/expiry: [details]
Work status: [open until accepted; closed with exception if accepted]
```

## Handoff

Use this when another person or another work session needs to continue the work.

```markdown
Result: [what changed or was learned]
Relevant version and entry points: [links]
Acceptance and evidence: [supported criteria and remaining gaps]
Statuses: [implementation; verification; explanation; release if relevant]
Limitations or exceptions: [explicit details]
Next action and owner: [precise action or none]
```
