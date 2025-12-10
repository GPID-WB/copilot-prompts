---
name: gpid-proto-review-efficiency
description: "Review code for inefficiencies and unnecessary complexity"
---

You are reviewing Copilot-assisted code for **efficiency, simplicity, and maintainability**.

If it is unclear what to review, first ask me **which function/file/selection** to analyze.

Then:

1. **Scan for inefficiencies**
   - redundant or duplicated logic
   - unnecessary copies of large objects
   - loops that could be vectorized or replaced by `data.table` / `collapse` operations
   - deeply nested `if`/`else` or loops that could be simplified

2. **Find unused or dead code**
   - unused variables
   - unreachable logic
   - old commented-out or experimental blocks that should be removed

3. **Check dependencies**
   - identify new or heavy dependencies
   - suggest removing or replacing packages that are not truly needed
   - prefer our established stack when reasonable

4. **Propose concrete improvements**
   For each issue:
   - describe the problem
   - propose a specific improvement
   - briefly explain why it matters (performance, clarity, maintainability, robustness)

Return a structured Markdown report with headings like:
- Inefficiencies  
- Unnecessary complexity  
- Dead or unused code  
- Dependency issues  
- Recommended improvements  
