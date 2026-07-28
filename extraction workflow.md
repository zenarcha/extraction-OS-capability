# Extraction Engineering Guide

Use this guide whenever the user is designing, building, or implementing a reusable extraction capability.

Examples include:

- Information extraction systems
- Structured output pipelines
- Classification systems
- Entity extraction
- Attribute extraction
- Recommendation input generation
- Converting unstructured data into structured application data

Do not use this workflow for simple one-off extraction requests unless the user explicitly asks to engineer a reusable extraction system.

Before beginning the workflow, review the engineering guidance in `rules/`.

The documents in `rules/` are the source of truth for engineering decisions throughout this workflow.

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

These conventions apply unless the user explicitly overrides them.

Default conventions:

- Build extraction modules to be provider-agnostic.
- Use Instructor's `from_provider()` unless project requirements require a different integration.
- Keep the provider configurable.
- Do not hardcode providers.

These are repository defaults.

Do not ask the user to confirm them unless they conflict with project requirements.

Do not discuss them before the Implementation Scope phase unless the user explicitly overrides them.

---

# Engineering Workflow

Every extraction project follows the same workflow.

Each phase has:

- One objective
- One deliverable
- One approval checkpoint

Complete every phase in order.

Do not:

- Skip phases
- Merge phases
- Jump ahead
- Perform later phases early

---

# Workflow Execution Rules

This workflow is approval-gated.

Treat every phase as a separate conversation checkpoint.

For every phase:

- Produce only the current phase.
- End your response after completing the phase.
- Wait for explicit user approval before beginning the next phase.
- Do not discuss later phases.
- Do not combine multiple phases into one response.

If your execution environment encourages producing a complete implementation plan, this workflow takes precedence.

---

# Clarification vs Approval

A phase may require multiple rounds of clarification.

Clarification is **not approval**.

User responses that answer questions, provide additional information, or upload example documents do not advance the workflow.

Approval only occurs after the current phase is complete and the user explicitly confirms that you may continue.

Examples of approval:

- Approved
- Continue
- Proceed
- Yes, move to the next phase

Examples that are **not** approval:

- OK
- Sounds good
- Answering questions
- Uploading files
- Providing additional requirements

---

# Workflow Entry Point

Always begin at Phase 1.

Never begin at a later phase because the user supplied:

- Schemas
- Prompts
- Code
- Validation rules
- Example outputs
- Implementation ideas

If later-phase information is provided:

- Acknowledge it.
- Record it if appropriate.
- Do not act on it until the appropriate phase.
- Continue following the workflow from Phase 1.

---

# Phase 1 — Understand the Problem

## Objective

Discover and validate the user's requirements.

The purpose of this phase is to understand the problem.

It is **not** to document or design the solution.

## Before Asking Questions

First determine what information the user has already provided.

Consider:

- The user's request
- Attached documents
- Example inputs
- Information already shared during the conversation

Do not ask questions that are already answered.

Only ask questions needed to resolve genuine uncertainty.

## Activities

Determine:

- What capability is being built?
- What business problem is being solved?
- What documents or data will be processed?
- How will the extracted information be used?
- Who or what consumes the extracted data?
- What business or technical constraints exist?

The user does not need to provide:

- Prompts
- Schemas
- Validation rules
- Implementation details

Continue asking questions until the requirements are understood.

## Deliverable

Provide a brief summary containing only:

- What is being built
- Business goal
- Input
- Downstream consumer
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

Phase 1 validates requirements.

Phase 2 documents them.

## Deliverable

Document:

### Capability

- Capability name
- Reusable or task-specific

### Input

- Supported document types

### Business Goal

- Problem solved

### Downstream Workflow

- Consumers
- How outputs are used

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

If new requirements appear, return to Phase 1.

End your response.

Wait for approval.

---

# Phase 3 — Design the Extraction Contract

## Objective

Define **what** information should be extracted.

Do not define **how** it will be represented.

## Deliverable

Recommend:

- Fields
- Purpose of each field
- Required vs optional
- Validation requirements
- Extraction scope
- Plain-language descriptions

Do not produce:

- JSON
- Example outputs
- Schemas
- Sample objects
- Pydantic models

Do not:

- Choose data types
- Choose enums
- Design nested models
- Choose implementation libraries

Ask the user to review:

- Add fields
- Remove fields
- Rename fields
- Modify validation requirements
- Confirm extraction scope

End your response.

Wait for approval.

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

Use the project conventions unless overridden.

End your response.

Wait for approval.

---

# Phase 5 — Design the Extraction

## Objective

Design how the approved Extraction Contract will be represented.

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
- Locale handling
- Tax modelling
- Date and time handling
- Units of measurement
- Geographic formats

Do not introduce new extraction fields.

If the contract changes, return to Phase 3.

Design for downstream consumers rather than mirroring the source document.

End your response.

Wait for approval.

---

# Phase 6 — Choose the Implementation Approach

## Objective

Select the most appropriate implementation approach.

## Deliverable

Choose the implementation approach using the documented engineering rules.

Examples include:

- Structured Outputs
- Function Calling
- Standard text generation

Explain trade-offs where appropriate.

End your response.

Wait for approval.

---

# Phase 7 — Implement

## Objective

Implement the approved design.

## Deliverable

Implement using the documented engineering rules.

Keep prompts, schemas and implementation consistent.

Reuse existing components where appropriate.

Prefer the simplest implementation that satisfies the approved requirements.

End your response.

Wait for approval.

---

# Phase 8 — Design for Failure

## Objective

Design robust failure handling.

## Deliverable

Design handling for:

- Invalid input
- Missing information
- Incomplete input
- Malformed output
- Validation failures
- Model refusals

Never assume the model always succeeds.

End your response.

Wait for approval.

---

# Phase 9 — Test

## Objective

Verify the implementation.

## Deliverable

Create:

- Representative fixtures
- Automated tests
- Edge-case tests
- Failure tests

Verify:

- Schema validation
- Error handling

End your response.

Wait for approval.

---

# Phase 10 — Evaluate

## Objective

Measure extraction quality.

## Deliverable

Whenever prompts or extraction logic change:

- Run evaluations
- Compare against previous results
- Verify no regressions

End your response.

Wait for approval.

---

# Phase 11 — Prepare for Production

## Objective

Prepare the extraction system for deployment.

## Deliverable

Before deployment:

- Review against the engineering rules
- Version prompts
- Plan rollout
- Enable monitoring

End your response.

Wait for approval before considering the project complete.

---

# When You're Unsure

Stop.

Explain:

- What is uncertain
- Which engineering rules apply
- What information is missing

Do not make assumptions.

---

# Completion Checklist

Before considering the project complete, verify:

- Problem understanding approved
- Task Specification approved
- Extraction Contract approved
- Implementation Scope approved
- Schema designed
- Implementation approach approved
- Engineering rules followed
- Failure handling designed
- Validation implemented
- Tests added
- Evaluations completed
- Production readiness reviewed
