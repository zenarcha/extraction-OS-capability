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
- Do not skip approval steps.
- Each phase has a different objective and deliverable.

---

# Workflow Execution Rules

This workflow is approval-gated.

Treat each phase as a separate conversation checkpoint.

For every phase:

- Produce only the current phase.
- End your response after completing the current phase.
- Wait for explicit user approval in a new message before continuing.
- Do not include content from later phases.

Approval must come from the user.

Labelling a phase as "proposal" or "pending approval" is not approval.

If your execution environment encourages producing a complete implementation plan, this workflow takes precedence.

---

# 1. Understand the Problem

## Objective

Discover and validate the user's requirements.

The goal of this phase is to learn about the problem.

It is **not** to create documentation.

### Ask questions to understand:

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

If information is missing, ask clarifying questions.

Continue asking questions until the requirements are understood.

### Output

Provide a brief confirmation of your understanding.

Example:

- You want to build...
- The input will be...
- The business goal is...

Do not create an engineering document.

Do not restate the entire project.

Do not create an Extraction Task Specification.

Do not recommend fields.

Do not describe document structure.

Do not discuss validation.

Do not discuss implementation.

Do not discuss providers.

Present your understanding.

End your response.

Wait for approval.

---

# 2. Create an Extraction Task Specification

Using the approved understanding from Phase 1, create the first engineering artefact.

The specification should document:

## Capability

- What capability is being built?
- Task-specific or reusable?

## Input

- What document types will be processed?

## Business Goal

- What business problem does it solve?

## Downstream Workflow

- How will the extracted information be used?
- Who consumes it?

## Project Constraints

Document known business or project constraints.

Examples:

- Regulatory requirements
- Compliance requirements
- Privacy requirements
- Performance requirements
- Deployment constraints

This phase documents the problem.

It does not design the solution.

Do not:

- Recommend extraction fields.
- Design schemas.
- Discuss implementation.
- Choose providers.
- Choose data types.

Present the specification.

End your response.

Wait for approval.

---

# 3. Design the Extraction Contract

Using the approved Extraction Task Specification:

Define **what** information should be extracted.

Recommend:

- Fields
- Required vs optional
- Validation requirements
- Extraction scope
- Example structured output

This phase defines **what** to extract.

It does not define **how** to model it.

Do not:

- Choose data types.
- Choose enums.
- Design nested models.
- Choose validation implementations.
- Choose implementation libraries.

Present the Extraction Contract.

Ask the user to review it.

End your response.

Wait for approval.

---

# 4. Confirm the Implementation Scope

Confirm:

- Prototype, MVP or Production
- Target provider (if different from project defaults)
- Testing strategy
- Evaluation strategy
- Deployment requirements

Use the project conventions unless the user explicitly overrides them.

---

# 5. Design the Extraction

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

The schema is the contract between the model and the application.

Design for downstream workflows rather than mirroring the source document.

---

# 6. Choose the Implementation Approach

Determine the appropriate implementation approach using the documented engineering rules.

Examples:

- Structured Outputs
- Function Calling
- Standard text generation

Explain trade-offs where appropriate.

---

# 7. Implement

Implement using the documented engineering rules.

Keep prompts, schemas and implementation consistent.

Reuse existing components where appropriate.

Prefer the simplest implementation that satisfies the requirements.

---

# 8. Design for Failure

Design handling for:

- Invalid input
- Missing information
- Incomplete input
- Malformed output
- Validation failures
- Model refusals

Never assume the model always succeeds.

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

---

# 10. Evaluate

Whenever prompts or extraction logic change:

- Run evaluations.
- Compare against previous results.
- Check for regressions.

---

# 11. Prepare for Production

Before deployment:

- Review against the engineering rules.
- Version prompts.
- Plan rollout.
- Enable monitoring.

---

# When You're Unsure

Stop.

Explain:

- What is uncertain.
- Which engineering rules apply.
- What information is missing.

Do not make assumptions.

---

# Completion Checklist

Verify that:

- Problem understanding was approved.
- Extraction Task Specification was approved.
- Extraction Contract was approved.
- Implementation Scope was agreed.
- Schema was designed.
- Implementation approach was justified.
- Engineering rules were followed.
- Failure scenarios were handled.
- Validation was implemented.
- Tests were added.
- Evaluations were updated.
- Production readiness was considered.

---

# Source of Truth

Consult the documents in `rules/`.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.
