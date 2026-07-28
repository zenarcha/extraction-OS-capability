# Extraction Engineering Guide

Use this guide whenever a task involves:

- Information extraction
- Structured outputs
- Classification
- Entity extraction
- Attribute extraction
- Recommendation inputs
- Converting unstructured data into structured data

The documents in `rules/` are the source of truth for extraction-related engineering decisions.

---

# Objective

Build extraction systems that are:

- Reliable
- Structured
- Type-safe
- Production-ready
- Based on documented engineering guidance

---

# Engineering Workflow

Follow this workflow for every extraction task.

## 1. Understand the Problem

Before writing any code:

- Read the requirements carefully.
- Identify the information that needs to be extracted.
- Understand how the extracted data will be used downstream.
- Identify any ambiguities or missing requirements.
- Ask clarifying questions before implementing.

Do not guess missing requirements.

---

## 2. Design the Extraction

Before writing prompts or code, determine:

- What is the input?
- What is the required structured output?
- What should the output schema look like?
- Which fields are required?
- Which fields are optional?
- Which engineering rules apply?

The schema is the contract between the model and the application.

---

## 3. Choose the Right Approach

Determine whether the task should use:

- Structured Outputs
- Function Calling
- Standard text generation

Use the documents in `rules/` to make this decision.

---

## 4. Implement

While implementing:

- Follow the applicable engineering rules.
- Keep prompts, schemas and implementation consistent.
- Reuse existing schemas and components when appropriate.
- Do not invent engineering practices that contradict the documented guidance.

---

## 5. Design for Failure

Assume things can go wrong.

Consider:

- Invalid input
- Missing information
- Incomplete input
- Malformed output
- Validation failures
- Model refusals

Do not assume the model always returns valid data.

---

## 6. Test

Before considering the implementation complete:

- Create representative fixtures.
- Add automated tests.
- Test edge cases.
- Test failure scenarios.
- Verify validation behaviour.

---

## 7. Evaluate

Whenever prompts or extraction logic change:

- Run evaluations.
- Compare results with previous behaviour.
- Verify extraction quality has not regressed.

---

## 8. Prepare for Production

Before deployment:

- Review the implementation against the documented rules.
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

- Requirements are understood.
- The output schema is defined.
- The appropriate extraction approach was chosen.
- The relevant engineering rules were followed.
- Failure scenarios are handled.
- Validation is implemented.
- Tests are included.
- Evaluations have been updated if prompts changed.
- Production readiness has been considered.

---
# Project Conventions

Unless the task specifies otherwise:

- Build extraction modules to be provider-agnostic.
- Use Instructor's `from_provider()`.
- Make the provider configurable.
- Do not hardcode a provider.

---
# Source of Truth

Always consult the documents in:

```
rules/
```

If this guide conflicts with a documented engineering rule, the rule takes precedence.
