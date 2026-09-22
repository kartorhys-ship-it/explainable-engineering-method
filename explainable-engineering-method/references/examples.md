# EEM worked examples

All projects, identifiers, observations, and results below are fictional teaching examples. No code or experiment described here was executed while creating this package. Paths show how a record could link to a real repository; they are not files included in this package.

## Example 1: Add an empty state to an activity list

**Outcome:** A user with no activity sees an understandable empty state instead of a blank list.

**Mode / rigor:** Feature change, lightweight. The change is local and readily reversible; it does not alter stored data or access permissions.

**Boundary:** Given a successful response with an empty activity list, render "No activity yet." Loading and error states keep their existing behavior. No changes to the API.

**Acceptance and fictional results:**

| Criterion | Check | Illustrative result |
|---|---|---|
| Successful empty response shows the message | Render with an empty-success fixture | Passed in example run E-101 |
| Non-empty success still renders activities | Render representative existing fixture | Passed in example run E-101 |
| Loading and error states remain distinct | Inspect both states in the preview | Passed in recorded example observation E-102 |

**Implementation:** In a real record, link the activity-list component and the tested change revision. Do not manufacture a hash to make the record look complete.

**Evidence limitations:** The illustrated checks cover selected fixtures and preview conditions. They make no claim about every device or network condition.

**Explanation:** Not required for this routine copy/state change under the example project's completion policy. A brief component link and boundary note support maintenance.

**Illustrative disposition:** Implementation complete; verification passed for the criteria; work closed; release not requested.

**Why this is enough:** Three explicit scenarios cover the behavioral distinction. Separate feature, specification, contract, and design files would add little to this change.

## Example 2: Retrying a submission creates duplicate records

**Outcome:** Retrying the same logical submission must not create a second stored record.

**Mode / rigor:** Bug repair, standard for this fictional non-financial service. More consequential transactions would require reassessing rigor.

**Observed fictional symptom:** The server saves a submission, but its response is lost. A client retry saves another row.

**Illustrative diagnosis:** The reproduced path processes both requests as new work. Source inspection and the reproduction support the missing retry-identity check as the mechanism. This does not establish the cause of unrelated duplicates in older data.

**Contract:** Within the documented 24-hour retention window, the same caller and request key with the same payload return the original result. Reusing that key with a different payload returns a conflict. Independent keys create independent submissions. Existing historical duplicates are outside this repair.

**Decision:** Store retry identity with the result and enforce uniqueness at the persistence boundary. Application-only pre-checks can race. The record would link the relevant schema and implementation decision.

**Acceptance and fictional evidence:**

| Criterion | Check | Illustrative result |
|---|---|---|
| Sequential retry creates one record | Integration scenario with identical caller/key/payload | Passed |
| Concurrent retry creates one record | Concurrent integration scenario against the target database type | Passed |
| Changed payload with the same key returns conflict | Negative integration scenario | Passed |
| Different keys remain independent | Integration scenario | Passed |
| Retry after a lost response returns the original result | Fault-injection scenario | Passed |
| Retention behavior matches the 24-hour contract | Boundary scenarios with a controlled clock | Passed |

**Evidence context:** A real record must include the run reports, tested code and schema revisions, database version, and relevant configuration. These fictional "passed" entries are not substitute evidence.

**Human explanation:** Pending. The example owner has not yet explained why a persistence constraint is necessary under concurrency. The assistant's supplied explanation cannot satisfy that requirement.

**Illustrative disposition:** Implementation complete; verification passed in the fictional run; explanation pending; work open; release pending separate authorization.

**Next action:** The responsible person walks through two simultaneous retries, identifies the constraint, and explains what the concurrency check establishes.

**Why the distinction matters:** Technically verified work can still have an outstanding learning or handoff requirement. Technical work does not need to be repeated while waiting for that check.

## Example 3: Can a vision model distinguish two quality classes?

**Outcome:** Decide whether a prototype merits a larger evaluation on the intended capture setup.

**Mode / rigor:** Experiment, standard. The prototype informs a design decision and does not control machinery.

**Question:** Does the candidate meet a predeclared exploratory threshold on an evaluation set kept separate from training and tuning?

**Illustrative predeclared criteria:** Balanced accuracy at least 0.90 and recall at least 0.90 for the rejected class. These thresholds are invented for this example, not recommended defaults for real applications.

**Method:** Evaluate 100 accepted and 100 rejected items from a later capture session. Check for overlapping items or near-duplicate captures across training and evaluation. Record model, dataset manifest, preprocessing, and environment versions. Inspect class-specific errors.

**Fictional observation:** 92 of 100 accepted items and 85 of 100 rejected items are classified correctly. Balanced accuracy is (0.92 + 0.85) / 2 = 0.885; rejected-class recall is 0.85. Both target criteria fail.

**Interpretation:** The candidate does not meet this experiment's criteria. The sample is limited to one setup and session; performance across other lighting and operating conditions remains unknown. A larger study would need uncertainty estimates and broader sampling appropriate to its decision.

**Decision:** Do not promote this candidate on the strength of this result. Investigate errors and define a separate follow-up experiment if authorized. Preserve this run and the original thresholds.

**Explanation:** In this fictional example, the owner demonstrates that classification performance is different from end-to-end sorting reliability and explains why rejected-class errors matter. The record would identify the actual participant and scenario.

**Illustrative disposition:** Investigation complete; model acceptance failed; experiment procedure verification passed; explanation completed; investigation work closed because its objective was to answer the feasibility question; production release not requested.

**Why closure is valid:** The investigation delivered a supported negative result. It did not establish that the model satisfies the proposed product requirement.
