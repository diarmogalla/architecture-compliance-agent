
## CONCERNS.md Template (concerns focus)

```markdown
# Codebase Concerns

**Analysis Date:** [YYYY-MM-DD]
## Tech Debt & Technical Burden

This section assesses technical burden against the **NHSE Tech Guidelines** core principles and identifies areas requiring remediation. Reference: `docs/codebase/CONCERNS.md`

### Principle Alignment Assessment

#### I. Mainstream, Governed Platform Adoption

**Compliance Status:** [✓ Aligned / ⚠ Partial / ✗ Misaligned]

**Non-mainstream Technologies:**
- [Technology/Tool]: `[file paths]` — [Justification/ADR reference or remediation plan]
- [Technology/Tool]: `[file paths]` — [Justification/ADR reference or remediation plan]

**Legacy or Unsupported Tools:**
- [Tool]: `[file paths]` — Impact: [What degrades] — Migration path: [Target mainstream alternative]

---

#### II. Security, Compliance, and Dependency Hygiene by Default

**Compliance Status:** [✓ Aligned / ⚠ Partial / ✗ Misaligned]

**Security Scanning Gaps:**
- [Component/Module]: `[file paths]` — Gap: [What's not scanned] — Fix: [How to enable]

**Dependency Management Issues:**
- [Package]: `[file]` — Risk: [Why at risk] — Action: [Update/Replace/Audit]

**Secret/Credential Leaks:**
- [Incident]: Location: `[file paths]` — Status: [Remediated/Pending] — Mitigation: [Current controls]

---

#### III. Independent, Incremental Delivery

**Compliance Status:** [✓ Aligned / ⚠ Partial / ✗ Misaligned]

**Monolithic/Coupled Areas:**
- [Component/Module]: `[file paths]` — Problem: [Why tightly coupled] — Refactor plan: [How to decompose]
- [Component/Module]: `[file paths]` — Problem: [Why tightly coupled] — Refactor plan: [How to decompose]

**Untestable or Hard-to-Isolate Code:**
- [Functionality]: `[file paths]` — Barrier: [What prevents independent testing] — Solution: [Dependency injection / mock strategy / extraction]

---

#### IV. Automated Quality, Observability, and Governance

**Compliance Status:** [✓ Aligned / ⚠ Partial / ✗ Misaligned]

**Testing Gaps:**
- [Untested area]: `[file paths]` — Risk: High/Medium/Low — Coverage plan: [Unit/Integration/E2E needed]

**Observability Blind Spots:**
- [Component/Function]: `[file paths]` — Missing: [Logs/Metrics/Traces] — Instrumentation plan: [What to add]

**CI/CD Gate Weaknesses:**
- [Pipeline stage]: Issue: [What's not gated] — Remediation: [Add scan/test/validation]

---

#### V. Simplicity, Explicit Architecture, and Maintainability

**Compliance Status:** [✓ Aligned / ⚠ Partial / ✗ Misaligned]

**Over-Complex Patterns:**
- [Pattern/Abstraction]: `[file paths]` — Complexity: [Why hard to maintain] — Simplification: [Alternative approach]

**Undocumented Design Decisions:**
- [Decision/Trade-off]: `[file paths]` — Gap: [What's not explained] — ADR needed: [Link or create]

**Performance or Scalability Concerns:**
- [Operation/Component]: `[file paths]` — Issue: [What degrades] — Improvement: [Optimization or refactor]

### Summary & Remediation Roadmap

| Principle | Status | Critical Issues | Timeline |
|-----------|--------|-----------------|----------|
| Mainstream Adoption | [✓/⚠/✗] | [Count] | [Q#/Sprint] |
| Security & Hygiene | [✓/⚠/✗] | [Count] | [Q#/Sprint] |
| Independent Delivery | [✓/⚠/✗] | [Count] | [Q#/Sprint] |
| Quality & Observability | [✓/⚠/✗] | [Count] | [Q#/Sprint] |
| Simplicity & Maintainability | [✓/⚠/✗] | [Count] | [Q#/Sprint] |

**High-Priority Remediations:**
1. [Issue]: Blocks [What] — Target: [Date] — Owner: [Role]
2. [Issue]: Blocks [What] — Target: [Date] — Owner: [Role]

**Deferred or Accepted Technical Debt:**
- [Issue]: Reason: [Why accepted] — Review date: [When to revisit] — ADR: [Link]
- [Issue]: Reason: [Why accepted] — Review date: [When to revisit] — ADR: [Link]
---

*Concerns audit: [date]*