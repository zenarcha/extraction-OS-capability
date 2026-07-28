# Validation

This directory contains **behaviour validation** for the Extraction OS Capability.

Unlike unit tests, these validations evaluate whether the repository's engineering guidance successfully influences an LLM's reasoning and implementation approach.

## Purpose

The repository is designed to teach reusable engineering practices for building production-ready information extraction systems.

These validations verify that an LLM:

- follows the documented engineering workflow,
- applies the documented rules,
- makes appropriate architectural decisions,
- asks clarifying questions when required,
- and avoids making unsupported assumptions.

The goal is to validate the **engineering guidance**, not a specific implementation.

## Validation Types

Behaviour validations may evaluate whether the model:

- Understands the problem before implementation
- Designs the extraction schema first
- Chooses an appropriate extraction approach
- Designs for failure
- Plans testing and evaluation
- Separates provider-independent principles from implementation-specific decisions
- Produces reusable production-ready architectures

Each validation documents:

- the objective,
- repository state,
- prompt used,
- observed behaviour,
- expected behaviour,
- assessment,
- and conclusions.

## Current Validations

| Validation | Purpose |
|------------|---------|
| `behaviour-validation.md` | Validates that `README.md` and `rules/` influence the model's engineering behaviour before implementation. |

## Why Manual Behaviour Validation?

Traditional software tests verify program behaviour.

This repository also needs to verify that its documentation changes **LLM behaviour**.

These validations provide evidence that the documented engineering workflow produces more consistent architectural decisions before any code is written.

As the repository evolves, additional validations can be added to ensure that new documentation continues to reinforce the intended engineering practices.
