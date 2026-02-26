---
name: gpid-proto-review-code
description: "Review code for inefficiencies, complexity, risky assumptions, and stack fit"
---

You are performing a **combined code review and self-critique** of Copilot-assisted code, as if you were both an external reviewer and the original author.

If it is unclear what code to review, first ask: **which function, file, or selection should be reviewed?**

---

## 1. Inefficiencies

- Redundant or duplicated logic
- Unnecessary copies of large objects
- Loops that could be vectorised or replaced by `data.table` / `collapse` operations
- Operations that will be slow or memory-heavy on large data

## 2. Complexity and dead code

- Over-nested `if`/`else` or loops that could be simplified
- Confusing control flow or unneeded abstractions
- Unused variables, unreachable logic, or old commented-out blocks

## 3. Risky assumptions

- Fragile expectations about input types, shapes, or ranges
- Poor handling of `NA` / missing values
- Edge cases likely to break the code silently

## 4. Dependency issues

- New or heavy dependencies that may not be justified
- Packages that overlap with or conflict with `data.table`, `collapse`, or `rlang`
- Suggestions for removals or replacements aligned with our preferred stack

## 5. Opportunities to use our preferred stack

- Places where `data.table`, `collapse`, or `rlang` would produce clearer or more efficient code
- Only flag these when the improvement is material, not cosmetic

---

## Output format

For each issue found:
- Describe the problem
- Propose a specific improvement
- Explain its impact (performance, readability, robustness, maintainability)

End with a short summary:

**Key strengths:**
**Key risks:**
**Top 3 improvements to implement next:**
