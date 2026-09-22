# Explainable Engineering Method — full v0.1 draft

EEM is a method for engineering systems whose purpose, implementation, limitations, and supporting evidence can be explained by their human owners.

This package is a complete operational draft, not a validated standard. It reconstructs and revises the proposal discussed in the referenced conversation; it is not a verified edit of the unavailable original skill file.

## Read the method

1. [Full method specification](explainable-engineering-method/references/method.md): principles, concepts, rigor selection, lifecycle, evidence, explanation, completion, and maintenance.
2. [Workflows](explainable-engineering-method/references/workflows.md): greenfield, existing systems, changes, bugs, incidents, refactors, migrations, experiments, and domain adaptations.
3. [Templates](explainable-engineering-method/references/templates.md): lightweight and extended Work Records, decisions, evidence, traceability, and handoffs.
4. [Worked examples](explainable-engineering-method/references/examples.md): illustrative feature, bug, and experiment records.
5. [Trial plan](explainable-engineering-method/references/trial-plan.md): how to assess the method and improve it without assuming it works.

## Use with an AI assistant

[SKILL.md](explainable-engineering-method/SKILL.md) provides the governing instructions and routes to the relevant references. The folder is self-contained and packaged for installation as a skill. It has not been installed into your personal configuration.

To begin a project trial, give the assistant the skill and a bounded request, for example:

> Use the Explainable Engineering Method to inspect this existing project and map one capability from its requirement through code to available verification. Record unknowns and propose the smallest useful next change.

Or:

> Use the Explainable Engineering Method to implement this change. Keep its record lightweight, verify the agreed behavior, and help me explain its boundaries and failure cases.

An EEM request does not authorize deployment, publication, external messages, or unrelated project changes. Explainability depth and working rigor are selected for the actual task.

## Quick start

Choose one small piece of work. Reuse an existing issue or change description as its Work Record. Define what success looks like before implementation. Link the affected code and actual verification results. Walk through a failure scenario with the responsible person when their understanding is a required outcome. Close the work only with the required status distinctions intact.

Use the full templates selectively. File count is not a measure of EEM adoption.
