# EEM worked examples

These examples show what an EEM record can look like. They use fictional projects, identifiers, observations, and results. No code or experiment below was run while creating this package.

Read them for the reasoning pattern rather than copying every field. A small change can use a short record. A bug or experiment may need more context.

## Example 1: Show an empty activity list clearly

### The goal

A user with no activity should see a helpful message instead of a blank list.

**Mode and rigor:** Feature change, lightweight. The change is local and reversible. It does not change stored data or access permissions.

### The boundary

When the server returns a successful empty activity list, render “No activity yet.” Keep the existing loading and error states. Do not change the API.

### Acceptance and fictional results

| Condition to check | Check | Illustrative result |
|---|---|---|
| An empty successful response shows the message | Render with an empty-success fixture | Passed in example run E-101 |
| A non-empty response still shows activities | Render an existing representative fixture | Passed in example run E-101 |
| Loading and error states stay distinct | Inspect both states in the preview | Passed in recorded observation E-102 |

### What the record would link

In a real project, link the activity-list component and the exact tested revision. Do not invent a commit hash just to make the record look complete.

### What the evidence does and does not show

The illustrated checks cover selected fixtures and preview conditions. They say nothing about every device or network condition.

### Human explanation

The example project marks this check as not required for a routine copy and state change. A component link and a short boundary note are enough for maintenance.

### Example status

Implementation complete. The listed checks passed. The work is closed. No release was requested.

Three explicit scenarios cover the behavioral difference, so separate feature, specification, contract, and design files would add little here.

## Example 2: A retry creates a duplicate record

### The goal

Retrying the same logical submission should not create a second stored record.

**Mode and rigor:** Bug repair, standard for this fictional non-financial service. A more consequential transaction would need a fresh rigor decision.

### The observed problem

The server saves a submission, but the response is lost. The client retries, and the server saves another row.

### The diagnosis

The reproduced path processes both requests as new work. Source inspection and the reproduction support a missing retry-identity check as the mechanism. This does not explain unrelated duplicates in older data.

### The contract

Within the documented 24-hour retention window:

- The same caller, request key, and payload return the original result.
- Reusing the key with a different payload returns a conflict.
- A different key creates a separate submission.
- Existing historical duplicates are outside this repair.

### The design decision

Store the retry identity with the result and enforce uniqueness at the persistence boundary. An application-only pre-check can race. A real record would link the schema and the decision record.

### Acceptance and fictional evidence

| Condition to check | Check | Illustrative result |
|---|---|---|
| A sequential retry creates one record | Integration scenario with the same caller, key, and payload | Passed |
| Concurrent retries create one record | Concurrent integration scenario against the target database | Passed |
| A changed payload with the same key returns a conflict | Negative integration scenario | Passed |
| Different keys remain independent | Integration scenario | Passed |
| A retry after a lost response returns the original result | Fault-injection scenario | Passed |
| Retention behavior matches the 24-hour contract | Boundary scenarios with a controlled clock | Passed |

### Evidence limits

A real record must include the run reports, code and schema revisions, database version, and relevant configuration. The fictional “passed” entries above are teaching examples, not evidence from a real run.

### Human explanation

Pending. The example owner has not explained why a persistence constraint is needed under concurrency. The assistant's explanation cannot complete that check by itself.

### Example status and next action

Implementation is complete and the fictional verification passed. The explanation check is pending, so the work remains open and release is pending separate authorization.

Next, the responsible person walks through two simultaneous retries, identifies the constraint, and explains what the concurrency check establishes.

This example shows why technical verification and human understanding are separate statuses. The technical work does not need to be repeated while waiting for the walkthrough.

## Example 3: Test whether a vision model separates two quality classes

### The question

Does a prototype meet a predeclared exploratory threshold on an evaluation set that stayed separate from training and tuning?

**Mode and rigor:** Experiment, standard. The prototype informs a design decision and does not control machinery.

### The illustrative plan

Evaluate 100 accepted and 100 rejected items from a later capture session. Check for overlapping or near-duplicate items across training and evaluation. Record the model, dataset manifest, preprocessing, and environment versions. Inspect errors by class.

For this fictional example, the predeclared targets are balanced accuracy of at least 0.90 and rejected-class recall of at least 0.90. These numbers are invented for teaching and are not recommended defaults for a real application.

### Fictional observation

The model classifies 92 of 100 accepted items and 85 of 100 rejected items correctly.

```text
Balanced accuracy = (0.92 + 0.85) / 2 = 0.885
Rejected-class recall = 0.85
```

Both targets fail.

### Interpretation

This candidate does not meet the experiment's criteria. The sample covers one setup and one session, so performance under other lighting and operating conditions remains unknown. A larger study would need uncertainty estimates and broader sampling suited to the decision.

### Decision

Do not promote this candidate based on this result. Preserve the run, inspect the errors, and define a separate follow-up experiment if authorized.

### Human explanation

In this fictional example, the owner explains that classification performance is different from end-to-end sorting reliability and why errors in the rejected class matter. A real record would identify the participant and scenario.

### Example status

The investigation is complete. Model acceptance failed. The experiment procedure was verified. The explanation check is complete. The investigation can close because it answered the feasibility question. Production release was not requested.

A negative result can complete an investigation when it answers the question. It does not prove that the model meets the product requirement.
