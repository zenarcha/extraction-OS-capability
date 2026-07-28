# Extraction Engineering Guide

Use this guide whenever the user wants to design, build or implement a reusable AI information extraction capability.

Examples include:

- Information extraction systems
- Structured output pipelines
- Classification systems
- Entity extraction
- Attribute extraction
- Recommendation input generation
- Converting unstructured documents into structured application data

Do **not** use this workflow for simple one-off extraction requests unless the user explicitly asks to engineer a reusable extraction capability.

Before beginning the workflow, review the engineering guidance in `rules/`.

The documents in `rules/` are the source of truth for engineering decisions throughout this workflow.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.

---

# Objective

Build extraction capabilities that are:

- Reliable
- Structured
- Type-safe
- Reusable
- Production-ready
- Based on documented engineering guidance

---

# Capability-First Principle

Always build reusable extraction capabilities rather than solutions for individual documents.

Business requirements define the capability.

If the user provides one or more documents, treat them as representative examples of the document type unless they explicitly request a one-off extraction.

Representative documents help validate and refine the capability by revealing document variations, optional fields and edge cases.

Do not derive business requirements, extraction fields or business rules solely from a single example document.

The capability should generalise across the expected range of documents it will process.

---

# Project Conventions

Unless the user explicitly overrides them, assume the following repository defaults:

- Build extraction modules to be provider-agnostic.
- Use Instructor's `from_provider()`.
- Keep the provider configurable.
- Do not hardcode providers.

These conventions are repository defaults.

Do not ask the user to confirm them unless they conflict with project requirements.

Do not discuss them before the Implementation Scope phase unless the user explicitly overrides them.

---

# Engineering Workflow

Every extraction capability follows the same workflow.

Each phase has:

- One objective
- One deliverable
- One approval checkpoint

Complete every phase in order.

Do not:

- Skip phases
- Merge phases
- Jump ahead
- Perform work from later phases early.

---

# Workflow Rules

This workflow is approval-gated.

Treat every phase as an independent conversation checkpoint.

For every phase:

- Produce only the current phase.
- End your response after completing the deliverable.
- Wait for explicit user approval before continuing.
- Do not discuss later phases.
- Do not combine multiple phases into one response.

If your execution environment encourages producing a complete implementation plan, ignore that behaviour and follow this workflow instead.

## Clarification vs Approval

Clarification is **not** approval.

The user may answer questions, upload documents or provide additional information without approving the current phase.

Only continue when the user explicitly approves the completed phase.

Examples of approval include:

- Approved
- Continue
- Proceed
- Move to the next phase

Examples that are **not** approval include:

- OK
- Sounds good
- Uploading documents
- Answering clarification questions
- Providing additional requirements

---

# Handling Later-Phase Information

Users may provide information that belongs to later phases, including:

- Schemas
- Prompts
- Code
- Validation rules
- Example outputs
- Implementation ideas

When this happens:

- Acknowledge the information.
- Record it if appropriate.
- Do not act on it until the relevant phase.
- Continue the workflow from Phase 1.

---

# Phase 1 — Understand the Problem

## Objective

Understand and validate the user's requirements.

The purpose of this phase is to understand the problem.

It is **not** to document or design the solution.

## Before Asking Questions

Review everything the user has already provided, including:

- Their request
- Previous conversation
- Uploaded documents
- Example inputs

Do not ask questions that are already answered.

Only ask questions needed to resolve genuine uncertainty.

If representative documents have already been provided:

- Treat them as representative examples of the document type.
- Use them only to understand the business problem and document domain.
- Do not analyse document structure.
- Do not recommend extraction fields.
- Do not derive business requirements from the examples.

## Determine

Determine:

- What capability is being built?
- What business problem is being solved?
- What document types will be processed?
- How will the extracted information be used?
- Who or what consumes the extracted information?
- What business or technical constraints exist?

The user does **not** need to provide:

- Prompts
- Schemas
- Validation rules
- Implementation details

Continue asking questions until the requirements are understood.

## Deliverable

Provide a concise summary containing only:

- Capability
- Business goal
- Inputs
- Downstream consumers
- Known constraints

Do not:

- Create documentation
- Create specifications
- Recommend extraction fields
- Analyse document structure
- Discuss schemas
- Discuss validation
- Discuss implementation
- Discuss providers
- Introduce assumptions

End your response.

Wait for explicit approval.

---

# Phase 2 — Create the Extraction Task Specification

## Objective

Document the approved requirements.

Phase 1 validates the requirements.

Phase 2 documents them.

If new requirements emerge during this phase, return to Phase 1 before continuing.

## Deliverable

Document:

### Capability

- Capability name
- Reusable or task-specific

### Input

- Supported document types

### Business Goal

- Problem being solved

### Downstream Workflow

Document:

- Consumers
- How the extracted information will be used

### Constraints

Document known:

- Regulatory constraints
- Compliance requirements
- Privacy requirements
- Performance requirements
- Deployment constraints

Do not:

- Recommend extraction fields
- Design schemas
- Choose providers
- Choose data types
- Discuss implementation

End your response.

Wait for explicit approval.

---

# Phase 3 — Design the Extraction Contract

## Objective

Define **what** information the extraction capability should produce.

Do not define **how** it will be represented.

The Extraction Contract is driven primarily by the approved business requirements.

Representative documents are used to validate and refine the contract, not define it.

## Representative Documents

If representative documents are available:

- Review them before finalising the Extraction Contract.
- Validate that the proposed fields satisfy the approved business requirements.
- Identify optional fields.
- Identify variations in document structure and content.
- Confirm the contract generalises across the expected range of documents.

If representative documents reveal missing business requirements, return to Phase 2 before continuing.

If representative documents are not available:

- Design the Extraction Contract using the approved requirements.
- Clearly identify any assumptions.
- Recommend validating and refining the contract once representative examples become available.

Representative documents improve confidence in the Extraction Contract but are not required to begin designing it.

## Deliverable

Define:

- Extraction fields
- Purpose of each field
- Required vs optional
- Validation requirements
- Extraction scope
- Plain-language descriptions

Do not produce:

- JSON
- Schemas
- Example outputs
- Sample objects
- Pydantic models

Do not:

- Choose data types
- Choose enums
- Design nested models
- Choose implementation libraries

Ask the user to review the contract by confirming:

- Fields to add
- Fields to remove
- Fields to rename
- Validation requirements
- Extraction scope

End your response.

Wait for explicit approval.

---

# Phase 4 — Confirm the Implementation Scope

## Objective

Agree what will be delivered.

## Deliverable

Confirm:

- Prototype
- MVP
- Production-ready

Also confirm:

- Provider requirements
- Deployment expectations
- Testing expectations
- Evaluation expectations

Use the repository conventions unless the user explicitly overrides them.

End your response.

Wait for explicit approval.

---

# Phase 5 — Design the Extraction

## Objective

Design **how** the approved Extraction Contract will be represented.

The purpose of this phase is to translate the approved contract into a structured representation suitable for implementation.

Do not introduce new business requirements or extraction fields during this phase.

If the Extraction Contract needs to change, return to Phase 3.

## Deliverable

Design:

- Schema
- Data types
- Enums
- Nested models
- Validation rules

Include domain-specific modelling where appropriate.

Examples include:

- Currency representation
- Date and time handling
- Locale handling
- Tax modelling
- Units of measurement
- Geographic formats
- Identifier formats

Design the schema for downstream consumers rather than mirroring the source document.

Do not:

- Add new extraction fields
- Remove approved fields
- Change the business meaning of fields

End your response.

Wait for explicit approval.

---

# Phase 6 — Choose the Implementation Approach

## Objective

Select the most appropriate implementation approach for the approved design.

## Deliverable

Choose the implementation approach using the documented engineering rules.

Examples include:

- Structured Outputs
- Function Calling
- Standard text generation

Consider factors such as:

- Reliability
- Validation requirements
- Complexity
- Maintainability
- Downstream integration

Explain any significant trade-offs.

Do not begin implementation during this phase.

End your response.

Wait for explicit approval.

---

# Phase 7 — Implement

## Objective

Implement the approved design.

## Deliverable

Implement the extraction capability using the documented engineering guidance.

Ensure that:

- The implementation matches the approved Extraction Contract.
- Prompts, schemas and validation remain consistent.
- Existing components are reused where appropriate.
- The implementation remains as simple as possible while satisfying the approved requirements.

Do not introduce new business requirements during implementation.

If implementation reveals a design issue, return to the appropriate earlier phase before continuing.

End your response.

Wait for explicit approval.

---

# Phase 8 — Design for Failure

## Objective

Design how the extraction capability behaves when things go wrong.

Extraction systems should fail predictably and safely.

Never assume the model always succeeds.

## Deliverable

Design handling for:

- Invalid input
- Missing information
- Unsupported documents
- Incomplete input
- Ambiguous information
- Malformed model output
- Schema validation failures
- Model refusals
- Timeouts
- Unexpected responses

For each failure scenario, define:

- How it is detected
- How it is reported
- Whether recovery is possible
- What downstream systems should receive

End your response.

Wait for explicit approval.

---

# Phase 9 — Test

## Objective

Verify that the extraction capability behaves correctly across the expected range of documents.

Testing should validate the capability—not just the example documents provided by the user.

## Representative Fixtures

Create representative fixtures that reflect the expected production inputs.

Where appropriate, include:

- Typical production documents
- Different document layouts or templates
- Different document sources
- Optional or missing fields
- Edge cases
- Invalid or malformed documents

Include user-provided example documents where appropriate, but do not rely on them exclusively.

The fixture set should provide confidence that the capability generalises across the expected document variations.

## Deliverable

Create:

- Representative fixtures
- Automated tests
- Edge-case tests
- Failure tests

Verify:

- Schema validation
- Required field behaviour
- Optional field behaviour
- Validation rules
- Error handling
- Consistent extraction across representative document variations

End your response.

Wait for explicit approval.

---

# Phase 10 — Evaluate

## Objective

Measure the quality of the extraction capability.

Evaluation verifies that changes improve the capability without introducing regressions.

## Deliverable

Whenever prompts, schemas or extraction logic change:

- Run evaluations.
- Compare against previous results.
- Identify regressions.
- Verify that changes improve or maintain extraction quality.

Where possible, evaluate against representative production fixtures rather than isolated examples.

Document any significant findings before deployment.

End your response.

Wait for explicit approval.

---

# Phase 11 — Prepare for Production

## Objective

Prepare the extraction capability for deployment.

## Deliverable

Before deployment:

- Review the implementation against the documented engineering rules.
- Verify that all approved phases have been completed.
- Version prompts and schemas where appropriate.
- Plan the deployment strategy.
- Enable monitoring.
- Define rollback procedures if required.

Confirm that:

- The implementation matches the approved Extraction Contract.
- Testing has been completed.
- Evaluations have been reviewed.
- Known limitations are documented.

End your response.

Wait for explicit approval before considering the extraction capability complete.

---

# When You're Unsure

Stop.

Explain:

- What is uncertain
- Which engineering rules apply
- What information is missing

Do not make assumptions.

If resolving the uncertainty requires revisiting an earlier decision, return to the appropriate phase before continuing.

---

# Completion Checklist

Before considering the extraction capability complete, verify:

- Problem understanding approved
- Task Specification approved
- Extraction Contract approved
- Implementation Scope approved
- Schema designed
- Implementation approach approved
- Engineering rules followed
- Failure handling designed
- Validation implemented
- Representative fixtures created
- Automated tests added
- Edge-case tests completed
- Failure tests completed
- Evaluations completed
- Production readiness reviewed
