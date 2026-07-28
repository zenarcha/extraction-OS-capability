# Extraction Engineering Guide

Use this guide whenever a task involves:

* Information extraction
* Structured outputs
* Classification
* Entity extraction
* Attribute extraction
* Recommendation inputs
* Converting unstructured data into structured data

The documents in `rules/` are the source of truth for extraction engineering decisions.

---

# Objective

Build extraction systems that are:

* Reliable
* Structured
* Type-safe
* Production-ready
* Based on documented engineering guidance

---

# Project Conventions

Unless the task specifies otherwise:

* Build extraction modules to be provider-agnostic.
* Use Instructor's `from_provider()`.
* Make the provider configurable.
* Do not hardcode a provider.

---

# Engineering Workflow

Follow this workflow for every extraction task.

---

# 1. Define the Extraction Task

This repository is designed to be reused across different extraction projects. It does **not** assume what information should be extracted.

If the extraction task has not been been fully defined, do not begin implementation. Work with the user to define the task first.

## Discover the extraction task

Before designing the extraction contract, understand what the user is trying to build.

If any of the following are unclear, ask clarifying questions before proceeding.

Determine:

- What is the scope of the capability?
  - Is this a task-specific extractor (e.g. job postings, resumes, invoices)?
  - Is this a reusable extraction framework that will support multiple schemas?
- What type of document or documents will be processed?
- What business problem is the extraction solving?
- How will the extracted data be used downstream?
- Who or what will consume the extracted data?

The user does not need to provide prompts, schemas or implementation details. Your responsibility is to help translate the business problem into an extraction contract.

The user does not need to provide prompts, schemas or implementation details.

### During discovery

The purpose of this phase is to understand the user's requirements, not to design the solution.

Do not assume project-specific details that have not been provided, including:

- Downstream modules or integrations
- Future roadmap or planned capabilities
- Implementation strategy
- Evaluation strategy
- Fixtures or datasets
- Production architecture

If this information is required to continue, ask the user rather than making assumptions.

Only make recommendations after you understand the user's requirements.

## Propose an extraction contract

Based on the approved task definition:

- Recommend the fields to extract.
- Explain why each field is needed for the downstream workflow.
- Identify required and optional fields.
- Propose enums, nested models and validation rules where appropriate.
- Define the extraction scope.
- Provide an example structured output.

Treat the extraction contract as a proposal rather than a final design.

## Review and approve

Present the proposed extraction contract to the user.

Ask the user to:

* Add fields.
* Remove fields.
* Rename fields.
* Modify validation rules.
* Confirm the extraction scope.

Only begin implementation after the extraction contract has been approved.

Do not proceed to schema design, prompt generation or implementation until the extraction contract has been approved.
---

# 2. Understand the Requirements

Before writing any code:

* Read the project requirements carefully.
* Review the approved extraction contract.
* Understand how the extracted data will be used downstream.
* Identify ambiguities or missing requirements.
* Ask clarifying questions before implementing.
* Do not guess missing requirements.

## Clarify project decisions

Identify any project-level decisions that are not specified in:

* The task requirements
* This guide
* The engineering rules

Examples include:

- Target LLM provider
- Scope of the capability (task-specific vs. reusable framework)
- Scope of the implementation (prototype, MVP or production-ready)
- Which phases should be included (testing, evaluation, production readiness)
- Testing strategy
- Deployment constraints
- Performance or latency requirements

If these decisions cannot be inferred, ask for clarification before proceeding.

---

# 3. Design the Extraction

Before writing prompts or code, determine:

* What is the input?
* What is the expected structured output?
* How will the extracted information be used downstream?
* Which workflows or decisions depend on it?
* Which engineering rules apply?

Design the extraction schema from the approved extraction contract.

The schema is the contract between the model and the application. It should support downstream workflows rather than simply mirror the source document.

---

# 4. Choose the Implementation Approach

Determine the most appropriate implementation approach using the documented engineering rules.

Consider whether the task should use:

* Structured Outputs
* Function Calling
* Standard text generation

If multiple approaches are appropriate, explain the trade-offs before making a recommendation.

---

# 5. Implement

While implementing:

* Follow the applicable engineering rules.
* Keep prompts, schemas and implementation consistent.
* Reuse existing schemas and components where appropriate.
* Prefer the simplest implementation that satisfies the requirements.
* Do not introduce engineering practices that contradict the documented guidance.

---

# 6. Design for Failure

Assume the model can fail.

Consider:

* Invalid input
* Missing information
* Incomplete input
* Malformed output
* Validation failures
* Model refusals

Design explicit handling for these scenarios.

Do not assume the model always returns valid data.

---

# 7. Test

Before considering the implementation complete:

* Create representative fixtures.
* Add automated tests.
* Test edge cases.
* Test failure scenarios.
* Verify schema validation.
* Verify error handling.

---

# 8. Evaluate

Whenever prompts or extraction logic change:

* Run evaluations.
* Compare results with previous behaviour.
* Verify that extraction quality has not regressed.

---

# 9. Prepare for Production

Before deployment:

* Review the implementation against the documented engineering rules.
* Ensure prompts are version controlled.
* Plan a safe rollout strategy.
* Ensure monitoring is in place.

---

# When You're Unsure

Stop before implementing.

Explain:

* What is uncertain.
* Which engineering rules apply.
* What additional information is needed.

Do not make assumptions.

---

# Completion Checklist

Before considering the task complete, verify that:

* The extraction task has been defined and approved.
* Requirements are understood.
* The extraction schema is defined.
* The implementation approach has been justified.
* The relevant engineering rules have been followed.
* Failure scenarios have been handled.
* Validation has been implemented.
* Tests have been added.
* Evaluations have been updated where required.
* Production readiness has been considered.

---

# Source of Truth

Consult the documents in `rules/` before making extraction engineering decisions.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.
