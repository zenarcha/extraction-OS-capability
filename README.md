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

The AI will guide you through the complete engineering workflow.

---

# Approval-Gated Workflow

This repository follows an approval-gated engineering workflow.

Rather than generating an implementation immediately, the AI works through each engineering phase in sequence.

For every phase it will:

- Complete only the current phase.
- Present the deliverable.
- Wait for your approval.
- Continue only after approval.

This ensures implementation decisions are not made before the requirements have been fully understood.

---

# Engineering Workflow

Every extraction capability follows the same workflow.

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

The AI never skips phases or combines multiple phases into one response.

---

# Workflow Overview

| Phase | Purpose |
|--------|---------|
| Understand the Problem | Discover and validate the user's requirements. |
| Extraction Task Specification | Document the approved business requirements. |
| Extraction Contract | Define **what** information should be extracted. |
| Implementation Scope | Agree what will be built. |
| Extraction Design | Define **how** the extraction contract will be represented. |
| Implementation Approach | Select the most appropriate extraction technique. |
| Implementation | Build the extraction capability. |
| Failure Design | Design handling for invalid or incomplete outputs. |
| Testing | Verify correctness and reliability. |
| Evaluation | Measure extraction quality and regressions. |
| Production | Prepare the extraction capability for deployment. |

---

# How the AI Works

During the workflow the AI will:

1. Understand your requirements.
2. Ask clarification questions only when information is genuinely missing.
3. Avoid making assumptions.
4. Keep implementation decisions out of early phases.
5. Build the extraction capability using the documented engineering rules.
6. Test and evaluate the implementation before considering it complete.

---

# Repository Structure

```text
README.md

Extraction Engineering Guide.md

rules/
    ...
```

## Extraction Engineering Guide

Defines the approval-gated engineering workflow used for every extraction capability.

It explains:

- The engineering phases
- Approval checkpoints
- Responsibilities of each phase
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

Engineering decisions are guided by the documents in `rules/`.

If the Engineering Guide conflicts with a documented engineering rule, the documented engineering rule takes precedence.
