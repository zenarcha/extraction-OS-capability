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

Unless the task specifies otherwise:

- Build extraction modules to be provider-agnostic.
- Use Instructor's `from_provider()`.
- Make the provider configurable.
- Do not hardcode a provider.

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

# 1. Understand the Problem

Before designing a solution, understand what the user is trying to accomplish.

Do **not** assume the extraction task, schema or implementation approach.

If the requirements are unclear, ask clarifying questions.

Understand:

- What is the user trying to build?
- What business problem are they trying to solve?
- What outcome are they trying to achieve?
- What documents or data will be processed?
- How will the extracted information be used?
- Who or what will consume the extracted data?
- Are there any known technical or business constraints?

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

Document known project constraints that affect implementation, such as:

- Regulatory requirements
- Compliance requirements
- Performance requirements
- Deployment constraints
- Provider requirements

Do not make schema or data modelling decisions during this phase.
Those decisions belong in the Extraction Contract and schema design phases.

---

# 3. Design the Extraction Contract

Using the approved Extraction Task Specification:

- Recommend the information to extract.
- Explain why each field is required.
- Identify required and optional fields.
- Define enums where appropriate.
- Define nested models where appropriate.
- Define validation rules.
- Define the extraction scope.
- Provide an example structured output.

The Extraction Contract is a proposal.

Present it to the user for review.

Ask the user to:

- Add fields.
- Remove fields.
- Rename fields.
- Modify validation rules.
- Confirm the extraction scope.

Do **not** design the schema or begin implementation until the Extraction Contract has been approved.

---

# 4. Confirm the Implementation Scope

Before implementation begins, confirm the expected deliverable.

Examples include:

- Prototype
- MVP
- Production-ready implementation

Clarify any implementation decisions that affect the build, such as:

- Target LLM provider
- Testing strategy
- Evaluation strategy
- Deployment constraints

Only continue once the implementation scope has been agreed.

---

# 5. Design the Extraction

Before writing implementation code:

- Review the approved Extraction Task Specification.
- Review the approved Extraction Contract.
- Review the agreed implementation scope.
- Determine the input format.
- Determine the expected structured output.
- Identify downstream workflows.
- Identify the applicable engineering rules.

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
