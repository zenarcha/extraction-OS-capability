Extraction Engineering Guide

Use this guide whenever a task involves:

Information extraction
Structured outputs
Classification
Entity extraction
Attribute extraction
Recommendation inputs
Converting unstructured data into structured data

The documents in rules/ are the source of truth for extraction engineering decisions.

Objective

Build extraction systems that are:

Reliable
Structured
Type-safe
Production-ready
Based on documented engineering guidance
Project Conventions

Unless the task specifies otherwise:

Build extraction modules to be provider-agnostic.
Use Instructor's from_provider().
Make the provider configurable.
Do not hardcode a provider.
Engineering Workflow

Follow this workflow for every extraction task.

1. Define the Extraction Task

Every extraction project begins with an Extraction Task Specification.

If one has not been provided, work with the user to create it before designing the extraction contract or writing any implementation.

The user does not need to provide prompts, schemas or implementation details.

Your responsibility is to translate the user's requirements into an Extraction Task Specification.

Extraction Task Specification

The specification should define:

Capability
What is being built?
Is this a task-specific extractor or a reusable extraction framework?
Input
What type of document or documents will be processed?
Business Goal
What business problem is the extraction solving?
Downstream Workflow
How will the extracted data be used?
Who or what consumes the extracted data?
Project Decisions

Identify any project-level decisions that affect the implementation, such as:

Target LLM provider
Implementation scope (prototype, MVP or production-ready)
Testing strategy
Evaluation strategy
Deployment constraints
Performance or latency requirements

If required information is missing, ask the user before proceeding.

Do not assume project-specific architecture, downstream integrations, future roadmap or implementation details.

Only continue once the Extraction Task Specification has been confirmed.

2. Design the Extraction Contract

Using the approved Extraction Task Specification:

Recommend the fields to extract.
Explain why each field is required.
Identify required and optional fields.
Define enums and nested models where appropriate.
Define validation rules.
Define the extraction scope.
Provide an example structured output.

The extraction contract is a proposal.

Present it to the user for review.

Ask the user to:

Add fields.
Remove fields.
Rename fields.
Modify validation rules.
Confirm the extraction scope.

Do not begin implementation until the extraction contract has been approved.

3. Design the Extraction

Before writing implementation code:

Review the approved Extraction Task Specification.
Review the approved Extraction Contract.
Determine the input format.
Determine the expected structured output.
Identify downstream workflows and dependencies.
Identify the applicable engineering rules.

Design the extraction schema from the approved Extraction Contract.

The schema is the contract between the model and the application. It should support downstream workflows rather than simply mirror the source document.

4. Choose the Implementation Approach

Determine the most appropriate implementation approach using the documented engineering rules.

Consider whether the task should use:

Structured Outputs
Function Calling
Standard text generation

If multiple approaches are appropriate, explain the trade-offs before making a recommendation.

5. Implement

While implementing:

Follow the applicable engineering rules.
Keep prompts, schemas and implementation consistent.
Reuse existing schemas and components where appropriate.
Prefer the simplest implementation that satisfies the requirements.
Do not introduce engineering practices that contradict the documented guidance.
6. Design for Failure

Assume the model can fail.

Design explicit handling for:

Invalid input
Missing information
Incomplete input
Malformed output
Validation failures
Model refusals

Do not assume the model always returns valid data.

7. Test

Before considering the implementation complete:

Create representative fixtures.
Add automated tests.
Test edge cases.
Test failure scenarios.
Verify schema validation.
Verify error handling.
8. Evaluate

Whenever prompts or extraction logic change:

Run evaluations.
Compare results with previous behaviour.
Verify that extraction quality has not regressed.
9. Prepare for Production

Before deployment:

Review the implementation against the documented engineering rules.
Ensure prompts are version controlled.
Plan a safe rollout strategy.
Ensure monitoring is in place.
When You're Unsure

Stop before implementing.

Explain:

What is uncertain.
Which engineering rules apply.
What additional information is needed.

Do not make assumptions.

Completion Checklist

Before considering the task complete, verify that:

An Extraction Task Specification has been created and approved.
An Extraction Contract has been created and approved.
The extraction schema has been defined.
The implementation approach has been justified.
The relevant engineering rules have been followed.
Failure scenarios have been handled.
Validation has been implemented.
Tests have been added.
Evaluations have been updated where required.
Production readiness has been considered.
Source of Truth

Consult the documents in rules/ before making extraction engineering decisions.

If this guide conflicts with a documented engineering rule, follow the documented engineering rule.
