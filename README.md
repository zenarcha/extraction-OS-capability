# AI Information Extraction Template

Build production-ready AI information extraction capabilities using a structured, approval-gated engineering workflow.

This repository helps you transform unstructured documents into reliable, validated, structured data using modern LLMs and reusable engineering patterns.

Typical use cases include:

- Job descriptions
- Resumes
- Invoices
- Contracts
- Customer support tickets
- Research papers
- Product catalogues
- Medical records
- Financial documents
- Any unstructured document that needs to become structured data

---

# Getting Started

Describe the extraction problem you want to solve.

Examples:

- I want to extract structured information from job descriptions.
- I need to extract invoice data into JSON.
- I want to classify customer support tickets.
- I want to extract entities from legal contracts.
- I need to build a reusable resume parser.

You do **not** need to:

- Design prompts
- Design schemas
- Decide which fields to extract
- Define validation rules
- Choose an extraction technique
- Select an implementation approach
- Provide sample documents immediately

The AI will guide you through the complete engineering workflow.

---

# Representative Documents

To design a robust extraction capability, the AI may request representative documents during the workflow.

Representative documents help identify:

- Common fields
- Optional fields
- Structural variations
- Validation requirements
- Edge cases

Recommended number of examples:

- **Minimum:** 3 representative documents
- **Recommended:** 5–10 representative documents
- **Complex or highly variable document types:** 10–20 representative documents

Where possible, provide documents that represent the range of inputs your extraction system will process, including:

- Different layouts or templates
- Documents from different sources
- Optional or missing fields
- Realistic production examples
- Edge cases

The AI will request these documents when they are needed. You do not need to provide them before starting the workflow.

---

# Approval-Gated Workflow

Every extraction project follows an approval-gated engineering workflow.

Rather than generating an implementation immediately, the AI works through each engineering phase in sequence.

For every phase it will:

- Complete only the current phase.
- Present the deliverable.
- Wait for your approval.
- Continue only after approval.

This prevents implementation decisions from being made before the requirements have been fully understood.

---

# Engineering Workflow

```text
Understand the Problem
          ↓
Extraction Task Specification
          ↓
Extraction Contract
          ↓
Implementation Scope
          ↓
Extraction Design
          ↓
Implementation Approach
          ↓
Implementation
          ↓
Failure Design
          ↓
Testing
          ↓
Evaluation
          ↓
Production
```

Each phase has:

- A single objective
- A single deliverable
- An approval checkpoint

The AI may request clarification or representative documents when they are required to complete the current phase.

---

# Workflow Overview

| Phase | Purpose |
|--------|---------|
| Understand the Problem | Discover and validate the business requirements. |
| Extraction Task Specification | Document the approved requirements. |
| Extraction Contract | Define what information should be extracted. |
| Implementation Scope | Agree what will be built. |
| Extraction Design | Decide how the extraction contract will be represented. |
| Implementation Approach | Select the most appropriate implementation technique. |
| Implementation | Build the extraction capability. |
| Failure Design | Handle invalid, incomplete and unexpected inputs. |
| Testing | Verify correctness, validation and reliability. |
| Evaluation | Measure extraction quality and detect regressions. |
| Production | Prepare the extraction capability for deployment. |

---

# How the AI Works

During the workflow the AI will:

1. Understand your business problem.
2. Use the information you've already provided before asking questions.
3. Ask clarification questions only when information is genuinely missing.
4. Request representative documents when they are needed to design the extraction capability.
5. Avoid making assumptions.
6. Keep implementation decisions out of the early phases.
7. Build the extraction capability using the documented engineering rules.
8. Test and evaluate the implementation before considering it complete.

---

# Repository Structure

```text
README.md

Extraction Engineering Guide.md

rules/
    ...
```

## Extraction Engineering Guide

Defines the approval-gated engineering workflow used for every extraction capability, including:

- Engineering phases
- Approval checkpoints
- Responsibilities
- Deliverables
- Workflow rules

## rules/

Contains the engineering guidance used throughout implementation, including:

- Prompt engineering
- Structured outputs
- Schema design
- Validation
- Testing
- Evaluation
- Production best practices

---

# Documentation

| Document | Purpose |
|----------|---------|
| `Extraction Engineering Guide.md` | Defines the end-to-end extraction engineering workflow. |
| `rules/` | Engineering guidance, implementation standards and best practices. |

---

# Source of Truth

The AI follows the workflow defined in the **Extraction Engineering Guide**.

Engineering and implementation decisions are guided by the documents in `rules/`.

If the Engineering Guide conflicts with a documented engineering rule, the documented engineering rule takes precedence.
