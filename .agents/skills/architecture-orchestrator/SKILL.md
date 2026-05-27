---
name: architecture-orchestrator
description: "Orchestrate repository onboarding by running acquire-codebase-knowledge first, then architecture-blueprint-generator and likec4-dsl. Validate that required architecture docs exist in docs/codebase/."
license: MIT
compatibility: "Cross-platform"
metadata:
  version: "1.0"
  depends-on:
    - acquire-codebase-knowledge
    - architecture-blueprint-generator
    - likec4-dsl
argument-hint: "Optional: specify whether docs should be validated under docs/codebase/. Default: docs/codebase/."
---

# Architecture Orchestrator

This skill orchestrates a multi-step architecture onboarding workflow for the repository.
It ensures the codebase knowledge acquisition step runs first, then uses that output to drive architecture blueprint generation and LikeC4 architecture-as-code creation.

## Workflow

1. Run `acquire-codebase-knowledge` first.
   - This is the required source-of-truth step.
   - Its output is used as input for the other two skills.

2. After acquisition completes, run the following in parallel if possible:
   - `architecture-blueprint-generator`
   - `likec4-dsl`

3. Validate the required docs exist in `docs/codebase/` after the acquire step:
   - `STACK.md`
   - `STRUCTURE.md`
   - `ARCHITECTURE.md`
   - `CONVENTIONS.md`
   - `INTEGRATIONS.md`
   - `TESTING.md`
   - `CONCERNS.md`

## Output Contract

The workflow is complete only when:

- `acquire-codebase-knowledge` has run successfully.
- `architecture-blueprint-generator` and `likec4-dsl` have run after acquisition.
- `docs/codebase/STACK.md`, `docs/codebase/STRUCTURE.md`, `docs/codebase/ARCHITECTURE.md`, `docs/codebase/CONVENTIONS.md`, `docs/codebase/INTEGRATIONS.md`, `docs/codebase/TESTING.md`, and `docs/codebase/CONCERNS.md` all exist.
- Any missing files are either created by the acquisition step or replaced with a placeholder containing `[TODO]` and/or `[ASK USER]`.

## Validation Checklist

- [ ] Acquire codebase knowledge first.
- [ ] Run architecture blueprint generation after acquisition.
- [ ] Run LikeC4 DSL creation after acquisition.
- [ ] Confirm all seven required docs exist in `docs/codebase/`.
- [ ] Recover any missing docs with placeholders or explicit questions.
- [ ] Summarize findings, evidence, and any `[ASK USER]` items.

## Notes

- `architecture-blueprint-generator` and `likec4-dsl` are independent once codebase knowledge is available, so they can run in parallel when it makes sense.
- The orchestrator validates the required docs in `docs/codebase/` only.
- Prefer evidence-based claims and avoid assumptions when generating architecture or documentation artifacts.
