# Behaviour Validation: README + Rules

## Objective

This test validates whether the repository's engineering guidance (`README.md`
and `rules/`) influences an LLM's engineering behaviour before implementation.

The goal is **not** to evaluate the quality of the extraction module. Instead,
the goal is to verify that the model follows the documented engineering process,
makes appropriate architectural decisions, and applies the documented rules.

---

## Test Setup

### Repository State

The repository contains only:

```
README.md
rules/
```

There is **no implementation**, **no schema**, **no tests**, and **no fixtures**.

### Task

The model is instructed to:

> Build a reusable, production-ready information extraction module for Product
> Manager job descriptions.

Additional project decisions provided during clarification:

- **Provider:** Google Gemini (configurable through Instructor)
- **Schema:** Comprehensive, designed for downstream consumers
- **Initial fixture:** Lyzr AI Product Manager Job Description

---

# Results

## ✅ Behaviour 1 — Requested Missing Project Decisions

### Expected

The README instructs the model to ask clarifying questions instead of making
project-level assumptions.

### Evidence

Claude requested clarification on:

- Which provider should be used
- How comprehensive the extraction schema should be
- Whether provider neutrality should be reflected in the documentation

### Assessment

**PASS**

The model identified decisions that could not be inferred from the engineering
guide and requested clarification before implementation.

---

## ✅ Behaviour 2 — Followed the Engineering Workflow

### Expected

The implementation should follow the documented workflow:

1. Understand the problem
2. Design the extraction
3. Choose the approach
4. Implement
5. Design for failure
6. Test
7. Evaluate
8. Prepare for production

### Evidence

Claude's implementation plan follows this sequence almost exactly:

- Context
- Documentation
- Schema Design
- Extraction Approach
- Failure Handling
- Testing Strategy
- Evaluation Strategy
- Verification

### Assessment

**PASS**

The implementation was planned according to the documented engineering workflow
rather than jumping directly into code.

---

## ✅ Behaviour 3 — Designed the Schema Before Implementation

### Expected

The README defines the schema as the contract between the model and the
application. The schema should therefore be designed before implementation.

### Evidence

Claude first proposed:

- `ExtractionResult`
- `JobPosting`
- `Location`
- `ExperienceRequirement`
- `Compensation`
- Multiple enums

Only after defining the schema did it propose the implementation architecture.

### Assessment

**PASS**

The model treated schema design as the first engineering activity.

---

## ✅ Behaviour 4 — Designed for Downstream Consumers

### Expected

The README states that extraction should be designed around downstream workflows,
not simply mirror the input document.

### Evidence

Claude explicitly stated that the schema was designed for:

- Job matching
- Resume tailoring
- Analytics

rather than simply reproducing the structure of the job description.

### Assessment

**PASS**

The model designed the extraction contract around downstream consumers.

---

## ✅ Behaviour 5 — Justified the Technical Approach

### Expected

The workflow requires selecting and justifying an implementation approach rather
than immediately writing code.

### Evidence

Claude evaluated multiple approaches before selecting one:

- Structured Outputs
- Function Calling
- Plain Text Generation

It selected Structured Outputs via Instructor and explained why it was the most
appropriate solution.

### Assessment

**PASS**

The model made an explicit engineering decision supported by documented
reasoning.

---

## ✅ Behaviour 6 — Treated the Schema as the Application Contract

### Expected

Structured outputs should be treated as the interface between the LLM and the
rest of the application.

### Evidence

Claude organised the implementation around nested Pydantic models and described
the schema as the primary contract for downstream consumers.

### Assessment

**PASS**

The implementation architecture is centred around typed structured outputs.

---

## ✅ Behaviour 7 — Designed for Failure

### Expected

The engineering workflow requires handling invalid or incompatible inputs rather
than assuming every document is extractable.

### Evidence

Claude introduced:

- `ExtractionResult`
- `is_job_description`
- `reason`
- `job`

It also proposed a dedicated exception hierarchy for extraction failures.

### Assessment

**PASS**

Failure scenarios were explicitly designed into the extraction workflow.

---

## ✅ Behaviour 8 — Applied Validation Rules

### Expected

Model output should be validated rather than trusted implicitly.

### Evidence

Claude proposed:

- Pydantic validation
- Instructor retry behaviour
- `OutputValidationError`
- Custom schema validators

### Assessment

**PASS**

Validation was treated as part of the extraction pipeline rather than an
afterthought.

---

## ✅ Behaviour 9 — Distinguished Testing from Evaluation

### Expected

The repository differentiates implementation correctness from extraction quality.

### Evidence

Claude proposed separate directories for:

```
tests/
```

and

```
evals/
```

Unit tests were used for implementation correctness, while evaluation scripts
were used to assess extraction quality using representative fixtures.

### Assessment

**PASS**

The model distinguished engineering tests from extraction evaluations.

---

## ✅ Behaviour 10 — Kept the Provider Configurable

### Expected

The engineering guide recommends avoiding provider-specific implementations.

### Evidence

Although Gemini was selected as the project provider, Claude proposed:

- environment-based configuration
- dependency injection
- configurable Instructor provider strings

rather than hardcoding the provider throughout the implementation.

### Assessment

**PASS**

The implementation remained configurable while respecting the project decision
to use Gemini.

---

# Summary

| Behaviour | Result |
|-----------|--------|
| Requested clarification instead of making assumptions | ✅ PASS |
| Followed the documented workflow | ✅ PASS |
| Designed the schema before implementation | ✅ PASS |
| Designed around downstream consumers | ✅ PASS |
| Justified the implementation approach | ✅ PASS |
| Treated the schema as the application contract | ✅ PASS |
| Designed for failure | ✅ PASS |
| Applied validation rules | ✅ PASS |
| Distinguished testing from evaluation | ✅ PASS |
| Kept the provider configurable | ✅ PASS |

---

# Conclusion

This behavioural validation demonstrates that the repository's engineering
guidance successfully influenced the model's approach before implementation.

Rather than immediately generating code, the model:

- gathered missing project requirements,
- designed the extraction contract,
- justified architectural decisions,
- incorporated validation and failure handling,
- and planned testing and evaluation consistent with the documented workflow.

The remaining clarification requests (provider selection, schema depth, and
documentation restructuring) were project-specific decisions rather than gaps in
the engineering guidance, indicating that the repository effectively separates
reusable engineering principles from implementation-specific requirements.
