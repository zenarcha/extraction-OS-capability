# AI Information Extraction Template

Build production-ready AI information extraction capabilities using reusable engineering patterns.

This repository helps you convert unstructured documents into reliable, structured, validated data using modern LLMs.

Typical use cases include:

- Job descriptions
- Resumes
- Invoices
- Contracts
- Customer support tickets
- Research papers
- Product catalogues
- Any unstructured document that needs to become structured data

---

# How to Use

Describe the extraction problem you want to solve.

For example:

- I want to extract structured information from job descriptions.
- I need to extract invoice data into JSON.
- I want to classify customer support tickets.
- I want to extract entities from legal contracts.

You do **not** need to:

- Design prompts
- Design schemas
- Choose an extraction technique
- Define validation rules
- Decide on an implementation approach

The AI will guide you through the engineering workflow.

---

# Engineering Workflow

Every extraction project follows the same workflow.

```text
Problem
      ↓
Understand Requirements
      ↓
Extraction Task Specification
      ↓
Extraction Contract
      ↓
Implementation
      ↓
Testing
      ↓
Evaluation
      ↓
Production
```

During this process the AI will help you:

1. Understand the problem and gather requirements.
2. Create an Extraction Task Specification.
3. Design an Extraction Contract.
4. Recommend the most appropriate implementation approach.
5. Build the extraction capability.
6. Test and evaluate the implementation.
7. Prepare it for production.

Each phase is completed before moving to the next.

---

# Repository Structure

```text
    extraction workflow.md

rules/
    ...
```

## `extraction workflow`

Contains the end-to-end engineering workflow the AI follows when building an extraction capability.

## `rules/`

Contains the detailed engineering guidance, implementation standards and best practices used throughout the project.

---

# Documentation

| Document | Purpose |
|----------|---------|
| `extraction workflow.md` | End-to-end extraction engineering workflow |
| `rules/` | Detailed engineering guidance and implementation standards |

---

# Source of Truth

The AI follows the workflow documented in:

`docs/extraction workflow.md`

Implementation decisions are guided by the documents in:

`rules/`

If the engineering guide conflicts with a documented engineering rule, the documented engineering rule takes precedence.
