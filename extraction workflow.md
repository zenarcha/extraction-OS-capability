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

Do not ask the user to confirm these conventions unless they conflict with the project requirements.

---

# Engineering Workflow

Follow this workflow for every extraction task.

---

# Workflow Principles

Treat each phase as a required checkpoint.

- Complete the current phase before moving to the next.
- Do not merge phases.
- Do not skip approval steps, even if you believe you have enough information to continue.

---

# Workflow Execution Rules

This workflow is **approval-gated**.

Treat each phase as a separate conversation checkpoint.

For every phase:

- Produce only the current phase.
- End your response after completing the current phase.
- Wait for explicit user approval in a new message before continuing.
- Do not include content from any later phase.
- Do not describe, propose, outline or draft future phases before they become active.

Approval must come from the user in a separate message.

Labelling a phase as **"proposal"**, **"pending approval"**, or **"needs approval"** does not count as approval.

If your execution environment encourages producing a complete implementation plan, this workflow takes precedence.

Do not combine phases or approval checkpoints.

---

# 1. Understand the Problem

Before designing a solution, understand what the user is trying to accomplish.

Do **not** assume:

- The extraction task
- The extraction schema
- The implementation approach

If the requirements are unclear, ask clarifying questions.

Understand:

- What is the user trying to build?
- What business problem are they trying to solve?
- What outcome are they trying to achieve?
- What documents or data will be processed?
- How will the extracted information be used?
- Who or what will consume the extracted data?
- Are there any known business or technical constraints?

The user does **not** need to provide:

- Prompts
- Schemas
- Validation rules
- Implementation details

Your responsibility is to translate the user's requirements into an engineering specification.

Do **not** infer project-specific details from:

- Previous examples
- Repository history
- Earlier conversations
- Existing modules

If required information is missing, ask the user before continuing.

---

# 2. Create an Extraction Task Specification

Once the requirements are understood, create an **Extraction Task Specification**.

The specification should define:

## Capability

- What capability is being built?
- Is it a task-specific extractor or a reusable extraction framework?

## Input

- What document type or document types will be processed?

## Business Goal

- What business problem does the extraction solve?

## Downstream Workflow

- How will the extracted information be used?
- Who or what consumes it?

## Project Constraints

Document known **business or project constraints** that influence the extraction capability.

Examples include:

- Regulatory requirements
- Compliance requirements
- Privacy requirements
- Performance requirements
- Deployment constraints

Do **not** ask about implementation technologies during this phase unless the user has already specified them.

Do **not** make:

- Schema decisions
- Data modelling decisions
- Provider decisions
- Implementation decisions

These belong in later phases.

Present the Extraction Task Specification to the user for review.

End your response after presenting this phase.

Wait for explicit user approval in a new message before continuing.

Do **not** continue to any later phase until the Extraction Task Specification has been approved.

Before sending your response, verify that it contains **only** the Extraction Task Specification.

---

# 3. Design the Extraction Contract

Using the approved Extraction Task Specification:

The Extraction Contract defines **what** information should be extracted.

It does **not** define how that information will be represented in code.

Recommend:

- The information to extract
- Why each field is required
- Required fields
- Optional fields
- Validation requirements
- The extraction scope
- An example structured output

The Extraction Contract is a proposal.

Present it to the user for review.

Ask the user to:

- Add fields
- Remove fields
- Rename fields
- Modify validation rules
- Confirm the extraction scope

Do **not** make schema decisions during this phase.

Do **not** define:

- Data types
- Enums
- Nested models
- Pydantic models
- Currency representation
- Locale handling
- Tax modelling
- Provider-specific implementation

Those decisions belong in the Design phase.

End your response after presenting this phase.

Wait for explicit user approval in a new message before continuing.

Do **not** continue to any later phase until the Extraction Contract has been approved.

This includes:

- Schema design
- Data modelling
- Implementation planning
- Project structure
- Testing strategy
- Evaluation planning
- Production planning

Before sending your response, verify that it contains **only** the Extraction Contract.

---

# 4. Confirm the Implementation Scope

Before implementation begins, confirm the expected deliverable.

Examples include:

- Prototype
- MVP
- Production-ready implementation

Clarify implementation decisions such as:

- Target LLM provider
- Provider-specific requirements
- Deployment environment
- Testing strategy
- Evaluation strategy

If the project conventions already define a default implementation, use those defaults unless the user explicitly requests otherwise.

Only continue once the implementation scope has been agreed.

---

# 5. Design the Extraction

Before writing implementation code:

Review:

- The approved Extraction Task Specification
- The approved Extraction Contract
- The agreed Implementation Scope

Determine:

- Input format
- Expected structured output
- Downstream workflows
- Applicable engineering rules

During this phase determine **how** the approved Extraction Contract will be represented.

Examples include:

- Data types
- Enums
- Nested models
- Validation rules
- Currency representation
- Locale handling
- Tax modelling

Design the extraction schema from the approved Extraction Contract.

The schema is the contract between the model and the application.

It should support downstream workflows rather than simply mirror the source document.

---

# 6. Choose the Implementation Approach

Determine the most appropriate implementation approach using the documented engineering rules.

Consider whether the task should use:

- Structured Outputs
- Function Calling
- Standard text generation

If multiple approaches are appropriate, explain the trade-offs before making a recommendation.

---

# 7. Implement

While implementing:

- Follow the documented engineering rules.
- Keep prompts, schemas and implementation consistent.
- Reuse existing schemas and components where appropriate.
- Prefer the simplest implementation that satisfies the requirements.
- Do not introduce engineering practices that contradict the documented guidance.

---

# 8. Design for Failure

Assume the model can fail.

Design explicit handling for:

- Invalid input
- Missing information
- Incomplete input
- Malformed output
- Validation failures
- Model refusals

Do not assume the model always returns valid data.

---

# 9. Test

Before considering the implementation complete:

- Create representative fixtures.
- Add automated tests.
- Test edge cases.
- Test failure scenarios.
- Verify schema validation.
- Verify error handling.

---

# 10. Evaluate

Whenever prompts or extraction logic change:

- Run evaluations.
- Compare results with previous behaviour.
- Verify that extraction quality has not regressed.

---

# 11. Prepare for Production

Before deployment:

- Review the implementation against the documented engineering rules.
- Ensure prompts are version controlled.
- Plan a safe rollout strategy.
- Ensure monitoring is in place.

---

# When You're Unsure

Stop before implementing.

Explain:

- What is uncertain.
- Which engineering rules apply.
- What additional information is needed.

Do not make assumptions.

---

# Completion Checklist

Before considering the task complete, verify that:

- The user's problem has been understood.
- An Extraction Task Specification has been created and approved.
- An Extraction Contract has been created and approved.
- The implementation scope has been agreed.
- The extraction schema has been defined.
- The implementation approach has been justified.
- The relevant engineering rules have been followed.
- Failure scenarios have been handled.
- Validation has been implemented.
- Tests have been added.
- Evaluations have been updated where required.
- Production readiness has been considered.

---

# Source of Truth

Consult the documents in `rules/` before making extraction engineering decisions.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.
