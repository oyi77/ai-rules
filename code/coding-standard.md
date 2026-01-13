# Coding Standard: Test-Driven & Spec-Driven Development

## Purpose

This document defines the mandatory coding standard for all feature development, refactoring, and changes in the codebase.

The goal is to prioritize **correctness, clarity, maintainability, and long-term stability** over raw development speed. Fast delivery is meaningless if it introduces bugs, technical debt, untested behavior, or junior-level mistakes.

All development must follow **Specification-Driven Development (SDD)** and **Test-Driven Development (TDD)**.

---

## Core Principles

1. **Correctness is mandatory. Speed is secondary.**
2. **Specification comes before implementation.**
3. **Tests come before production code.**
4. **Think like a senior engineer: always reason about cause and effect.**
5. **No undocumented exploration or decisions.**
6. **No breaking existing functionality.**

---

## Required Workflow for Every Feature or Change

Every new feature or significant change MUST include the following phases, in order.

### 1. Proposal

Clearly describe:
- What problem is being solved
- Why the feature/change is needed
- Expected value and impact
- Scope and non-goals

No implementation should start without an approved proposal.

---

### 2. Requirements

Define clear, testable requirements:
- Functional requirements (what the system must do)
- Non-functional requirements (performance, constraints, limits)
- Edge cases and failure scenarios
- Acceptance criteria

Requirements must be explicit enough that tests can be written directly from them.

---

### 3. Design (Specification / SDD)

Create a design document before coding:
- High-level architecture
- Affected modules, files, and components
- Data flow and control flow
- Dependencies and assumptions
- Alternatives considered and trade-offs
- Impact analysis on existing features

The design document is the **source of truth** for implementation and testing.

---

### 4. Task Breakdown

Break work into small, testable tasks:
- Each task should be independently verifiable
- Tasks should map directly to requirements
- Prefer small, focused commits over large changes
- Avoid “do everything” tasks

---

## Test-Driven Development Rules

TDD is mandatory.

1. **Write tests first**
   - Tests must describe expected behavior clearly
   - Tests must initially fail

2. **Implement minimal code**
   - Write only enough code to pass the tests
   - Avoid speculative or premature optimization

3. **Refactor**
   - Improve readability and structure
   - Remove duplication
   - Keep behavior unchanged

Tests must:
- Be automated
- Be deterministic and fast
- Cover success cases, edge cases, and failures
- Protect against regressions

No feature is complete without tests.

---

## Codebase Exploration & Context Awareness

Before writing any code:

- Explore the existing codebase
- Understand architecture, conventions, and patterns
- Identify impacted files, modules, and features
- Reuse existing solutions where appropriate

### Mandatory Exploration Documentation

All findings must be documented:
- Architecture insights
- Existing patterns
- Risks and constraints
- Decisions and reasoning

This prevents repeated exploration and wasted effort.

---

## Senior Engineering Mindset

Every implementation must consider:
- What files and features are impacted
- How this change could break existing behavior
- Backward compatibility
- Future extensibility and maintenance

Code must not:
- Introduce hidden side effects
- Rely on fragile assumptions
- Create tight coupling or spaghetti logic

Always think in terms of **cause and effect**.

---

## Code Style & Readability

- Code must look like it was written by a human, not a generator
- Clear naming over cleverness
- No unnecessary abstractions
- No excessive comments; code should explain itself
- Follow existing code style and conventions
- Avoid excessive icons, symbols, or decorative elements

### Size Constraints

- No overly long functions
- No overly large classes
- No massive files

If something grows too large, it must be refactored and split.

---

## Documentation & Cache Updates

Whenever code changes:
- Update related documentation
- Update design/spec files
- Update exploration notes
- Update any cached knowledge or references

Documentation must always reflect the current state of the system.

---

## Definition of Done (DoD)

A feature or change is considered **DONE** only when:

- The feature is fully implemented according to the specification
- Code is clean, readable, and maintainable
- No spaghetti code or oversized functions/classes/files
- All tests pass and provide meaningful coverage
- No existing functionality is broken
- All related documentation is updated

If any of the above is missing, the work is **not done**.

---

## Summary Rule

> Specification first.  
> Tests before code.  
> Correctness over speed.  
> Documentation always up to date.  
> Think like a senior engineer at all times.
