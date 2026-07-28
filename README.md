# Extraction Engineering Guide

This directory contains the engineering guidance for building reliable information extraction systems.

## Objective

Build extraction systems that are:

- Reliable
- Structured
- Type-safe
- Production-ready
- Based on documented engineering guidance

The documents in `rules/` are the source of truth for extraction-related implementation decisions.

---

# Workflow

Follow this process for every extraction task.

## 1. Understand the problem

Before writing code:

- Read the requirements.
- Identify what information needs to be extracted.
- Understand how the extracted data will be used.
- If requirements are ambiguous, ask clarifying questions before implementing.

Do not guess missing requirements.

---

## 2. Design the schema

Before writing prompts or code:

- Define the output schema.
- Decide which fields are required and optional.
- Use clear field names and types.
- Reuse existing schemas when appropriate.

The schema is the contract between the model and the application.

---

## 3. Choose the right approach

Determine whether the task requires:

- Structured Outputs
- Function Calling
- Standard text generation

Use the engineering rules to make this decision.

---

## 4. Implement

While implementing:

- Follow the applicable rules in the `rules/` directory.
- Do not invent engineering practices that contradict the documented guidance.
- Keep prompts, schemas and implementation consistent.

---

## 5. Handle failures

Design for failure.

Consider:

- invalid input
- incomplete input
- malformed output
- refusals
- validation failures

Do not assume the model always returns valid data.

---

## 6. Test

Before considering the implementation complete:

- Create representative fixtures.
- Add automated tests.
- Test edge cases.
- Test failure cases.
- Test validation behaviour.

---

## 7. Evaluate

When prompts or extraction logic change:

- Run evaluations.
- Compare against previous behaviour.
- Verify that extraction quality has not regressed.

---

## 8. Production readiness

Before deployment:

- Review the implementation against the documented rules.
- Ensure prompts are version controlled.
- Ensure monitoring is available.
- Plan safe rollout of prompt changes.

---

# When you're unsure

Stop and explain:

- what is uncertain
- which rules apply
- what information is missing

Do not make assumptions.

---

# Source of Truth

Always consult the documents in:

rules/

If this guide conflicts with a documented rule, the rule takes precedence.
