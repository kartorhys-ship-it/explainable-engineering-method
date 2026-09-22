# EEM templates

Copy only what the work needs. Bracketed text is an intentional field to fill, not a mandatory new file. Existing issue and pull-request formats may carry the same information.

## Lightweight Work Record

```markdown
# [ID or title]

Outcome: [useful result and reason]
Mode / rigor: [mode, level, one-sentence rationale]
Scope and boundaries: [change, relevant input/output, exclusions]

Acceptance:
- [observable condition]

Implementation: [source links and relevant revision/snapshot]
Verification: [criterion -> check -> actual result/evidence]
Limitations: [remaining uncertainty or none identified within checked scope]
Explanation: [completed / pending / not required; reason and scope]
Status: [implementation; verification; work disposition; release if relevant]
Next action: [action and owner, or none]
```

## Extended Work Record

```markdown
# [ID]: [title]

## Context
Outcome and source: [problem, user need, or investigation question]
Mode: [workflow]
Rigor: [level and reason]
Responsible people: [only roles whose ownership matters]
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
Design: [sufficient detail to understand the change]
Significant decisions: [links or short rationale]
Risks and recovery: [only relevant failure consequences and responses]

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

Do not write decision records for every routine implementation detail.

## Evidence record

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

Omit irrelevant version fields. Do not omit a version that materially changes the claim's meaning.

## Traceability view

```markdown
| Requirement or question | Work | Implementation boundary | Check | Evidence | Gap |
|---|---|---|---|---|---|
| [link] | [link] | [path/symbol/interface] | [link] | [versioned result] | [none or specific gap] |
```

Use multiple rows or linked lists for many-to-many relationships. Avoid forcing a single feature or test to represent a wider requirement.

## Human explanation record

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

## Exception record

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

```markdown
Result: [what changed or was learned]
Relevant version and entry points: [links]
Acceptance and evidence: [supported criteria and remaining gaps]
Statuses: [implementation; verification; explanation; release if relevant]
Limitations or exceptions: [explicit details]
Next action and owner: [precise action or none]
```
