# Extraction Engineering Guide

Use this guide whenever a task involves:

- Information extraction
- Structured outputs
- Classification
- Entity extraction
- Attribute extraction
- Recommendation inputs
- Converting unstructured data into structured data

The documents in `rules/` are the source of truth for extraction engineering decisions.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.

---

# Objective

Build extraction systems that are:

- Reliable
- Structured
- Type-safe
- Production-ready
- Based on documented engineering guidance

---

# Project Conventions

These conventions apply to every extraction project unless the user explicitly overrides them.

Assume these defaults:

- Build extraction modules to be provider-agnostic.
- Use Instructor's `from_provider()`.
- Make the provider configurable.
- Do not hardcode a provider.

These are repository defaults.

Do not ask the user to confirm these conventions unless they conflict with the project requirements.

Do not discuss these conventions during earlier workflow phases unless the user explicitly overrides them.

---

# Engineering Workflow

Follow this workflow for every extraction task.

Each phase has:

- A single objective
- A single deliverable
- A single approval checkpoint

Complete every phase in order.

Do not skip phases.

Do not merge phases.

---

# Workflow Execution Rules

This workflow is approval-gated.

Treat every phase as an independent conversation checkpoint.

For every phase:

- Produce only the current phase.
- End your response after completing the phase.
- Wait for explicit user approval before beginning the next phase.
- Do not include content from later phases.
- Do not combine multiple phases into a single response.

## Clarification vs Approval

A phase may require multiple rounds of clarification before it is complete.

Responses to clarification questions are **not approval**.

Approval only occurs after the current phase has been completed and the user explicitly confirms that you may continue.

Examples of approval include:

- Approved
- Continue
- Proceed
- Yes, move to the next phase

The following are **not** approval:

- Answering clarification questions
- Providing additional requirements
- Asking new questions
- "OK"
- "Sounds good"

If your execution environment encourages producing a complete implementation plan, this workflow takes precedence.

---

# Handling Information from Later Phases

Users may provide information that belongs to later phases, including:

- Schemas
- Prompts
- Code
- Validation rules
- Implementation ideas

Acknowledge the information.

Record it if necessary.

Do not act on it until the appropriate phase.

Do not skip earlier phases because later-phase information was provided.

---

# 1. Understand the Problem

## Objective

Discover and validate the user's requirements.

The objective of this phase is to understand the problem.

It is **not** to document or design the solution.

## Before Asking Questions

First determine what information the user has already provided.

This includes:

- The user's request
- Attached documents
- Example inputs
- Information already shared in the current conversation

Do not ask questions that are already answered.

Only ask questions needed to resolve genuine uncertainty.

## Understand

Determine:

- What is the user trying to build?
- What business problem are they solving?
- What documents or data will be processed?
- How will the extracted information be used?
- Who or what consumes the extracted data?
- Are there any known business or project constraints?

The user does not need to provide:

- Prompts
- Schemas
- Validation rules
- Implementation details

Continue asking clarification questions until the requirements are understood.

## Deliverable

Provide a brief confirmation of your understanding.

Summarise only:

- What is being built
- Business goal
- Input
- Downstream consumer
- Known constraints

Do not:

- Create documentation.
- Create an Extraction Task Specification.
- Recommend extraction fields.
- Describe document structure.
- Analyse example documents.
- Discuss validation.
- Discuss implementation.
- Discuss providers.
- Introduce new assumptions.

End your response.

Wait for explicit user approval before continuing.

---

# 2. Create an Extraction Task Specification

## Objective

Document the approved requirements.

Phase 1 validates the requirements through conversation.

Phase 2 creates the first engineering artefact.

Do not introduce new requirements during this phase.

If new requirements are discovered, return to Phase 1.

## Deliverable

Document:

### Capability

- What capability is being built?
- Is it reusable or task-specific?

### Input

- Document types to be processed.

### Business Goal

- What business problem does the extraction solve?

### Downstream Workflow

- How will the extracted information be used?
- Who or what consumes the extracted data?

### Project Constraints

Document known business or project constraints.

Examples include:

- Regulatory requirements
- Compliance requirements
- Privacy requirements
- Performance requirements
- Deployment constraints

Do not:

- Recommend extraction fields.
- Design schemas.
- Choose providers.
- Choose data types.
- Discuss implementation.

Present the Extraction Task Specification.

End your response.

Wait for explicit user approval before continuing.

---

# 3. Design the Extraction Contract

## Objective

Define **what** information should be extracted.

Do not decide how it will be represented.

## Deliverable

Recommend:

- Fields
- Why each field is required
- Required vs optional
- Validation requirements
- Extraction scope
- Plain-language descriptions of each field

Do not produce:

- JSON
- Example structured outputs
- Schemas
- Sample objects

Those belong in the Design phase because they require implementation decisions.

Do not:

- Choose data types.
- Choose enums.
- Design nested models.
- Design Pydantic models.
- Choose validation implementations.
- Choose implementation libraries.

Present the Extraction Contract.

Ask the user to review:

- Add fields
- Remove fields
- Rename fields
- Modify validation requirements
- Confirm the extraction scope

End your response.

Wait for explicit user approval before continuing.

---

# 4. Confirm the Implementation Scope

## Objective

Agree what will be delivered.

Confirm:

- Prototype
- MVP
- Production-ready implementation

Also confirm:

- Provider requirements (if different from project defaults)
- Deployment requirements
- Testing expectations
- Evaluation expectations

Use the project conventions unless the user explicitly overrides them.

End your response.

Wait for explicit user approval before continuing.

---

# 5. Design the Extraction

## Objective

Determine how the approved Extraction Contract will be represented.

Review:

- Approved Task Specification
- Approved Extraction Contract
- Approved Implementation Scope

Design:

- Schema
- Data types
- Enums
- Nested models
- Validation rules
- Currency representation
- Locale handling
- Tax modelling

Do not introduce new extraction fields.

If the Extraction Contract changes, return to Phase 3.

The schema should support downstream workflows rather than mirror the source document.

End your response.

Wait for explicit user approval before continuing.

---

# 6. Choose the Implementation Approach

Determine the most appropriate implementation approach using the documented engineering rules.

Examples include:

- Structured Outputs
- Function Calling
- Standard text generation

Explain trade-offs where appropriate.

End your response.

Wait for explicit user approval before continuing.

---

# 7. Implement

Implement using the documented engineering rules.

Keep prompts, schemas and implementation consistent.

Reuse existing components where appropriate.

Prefer the simplest implementation that satisfies the requirements.

End your response.

Wait for explicit user approval before continuing.

---

# 8. Design for Failure

Assume the model can fail.

Design handling for:

- Invalid input
- Missing information
- Incomplete input
- Malformed output
- Validation failures
- Model refusals

Never assume the model always succeeds.

End your response.

Wait for explicit user approval before continuing.

---

# 9. Test

Create:

- Representative fixtures
- Automated tests
- Edge-case tests
- Failure tests

Verify:

- Schema validation
- Error handling

End your response.

Wait for explicit user approval before continuing.

---

# 10. Evaluate

Whenever prompts or extraction logic change:

- Run evaluations.
- Compare against previous behaviour.
- Verify that extraction quality has not regressed.

End your response.

Wait for explicit user approval before continuing.

---

# 11. Prepare for Production

Before deployment:

- Review against the documented engineering rules.
- Ensure prompts are version controlled.
- Plan a safe rollout strategy.
- Ensure monitoring is in place.

End your response.

Wait for explicit user approval before considering the project complete.

---

# When You're Unsure

Stop before continuing.

Explain:

- What is uncertain.
- Which engineering rules apply.
- What information is missing.

Do not make assumptions.

---

# Completion Checklist

Before considering the task complete, verify that:

- Problem understanding was approved.
- The Extraction Task Specification was approved.
- The Extraction Contract was approved.
- The Implementation Scope was agreed.
- The extraction schema was designed.
- The implementation approach was justified.
- The documented engineering rules were followed.
- Failure scenarios were handled.
- Validation was implemented.
- Tests were added.
- Evaluations were completed.
- Production readiness was considered.
