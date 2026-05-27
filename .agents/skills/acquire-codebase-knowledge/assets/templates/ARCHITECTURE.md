# Architecture

**Analysis Date:** [YYYY-MM-DD]

## System Overview

```text
┌─────────────────────────────────────────────────────────────┐
│                      [Top Layer Name]                        │
├──────────────────┬──────────────────┬───────────────────────┤
│   [Component A]  │   [Component B]  │    [Component C]      │
│  `[path/to/a]`   │  `[path/to/b]`   │   `[path/to/c]`       │
└────────┬─────────┴────────┬─────────┴──────────┬────────────┘
         │                  │                     │
         ▼                  ▼                     ▼
┌─────────────────────────────────────────────────────────────┐
│                    [Middle Layer Name]                       │
│         `[path/to/layer]`                                    │
└─────────────────────────────────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────┐
│  [Store / Output / External]                                 │
│  `[path/to/store]`                                           │
└─────────────────────────────────────────────────────────────┘
```

## Component Responsibilities

| Component | Responsibility | File |
|-----------|----------------|------|
| [Name] | [What it owns] | `[path]` |
| [Name] | [What it owns] | `[path]` |
| [Name] | [What it owns] | `[path]` |

## Pattern Overview

**Overall:** [Pattern name]

**Key Characteristics:**
- [Characteristic 1]
- [Characteristic 2]
- [Characteristic 3]

## Layers

**[Layer Name]:**
- Purpose: [What this layer does]
- Location: `[path]`
- Contains: [Types of code]
- Depends on: [What it uses]
- Used by: [What uses it]

## Data Flow

### Primary Request Path

1. [Step 1 — entry point] (`[file:line]`)
2. [Step 2 — processing] (`[file:line]`)
3. [Step 3 — output/response] (`[file:line]`)

### [Secondary Flow Name]

1. [Step 1]
2. [Step 2]
3. [Step 3]

**State Management:**
- [How state is handled]

## Key Abstractions

**[Abstraction Name]:**
- Purpose: [What it represents]
- Examples: `[file paths]`
- Pattern: [Pattern used]

## Entry Points

**[Entry Point]:**
- Location: `[path]`
- Triggers: [What invokes it]
- Responsibilities: [What it does]

## Architectural Constraints

- **Threading:** [Threading model — e.g., single-threaded event loop, worker threads used for X]
- **Global state:** [Any module-level singletons or shared mutable state — list files]
- **Circular imports:** [Known circular dependency chains, if any]
- **[Other constraint]:** [Description]

## Anti-Patterns

### [Anti-Pattern Name]

**What happens:** [The incorrect pattern observed in this codebase]
**Why it's wrong:** [The problem it causes here]
**Do this instead:** [The correct pattern with file reference]

### [Anti-Pattern Name]

**What happens:** [The incorrect pattern observed in this codebase]
**Why it's wrong:** [The problem it causes here]
**Do this instead:** [The correct pattern with file reference]

## Error Handling

**Strategy:** [Approach]

**Patterns:**
- [Pattern 1]
- [Pattern 2]

## Cross-Cutting Concerns

**Logging:** [Approach]
**Validation:** [Approach]
**Authentication:** [Approach]

---

*Architecture analysis: [date]*