---
name: gpid-proto-self-critique
description: "Ask Copilot to critique its own generated code rigorously"
---

You are performing a **self-critique** of Copilot-assisted code, as if you were a human reviewer.

If it is unclear what code to review, first ask me **which function/file/selection** to critique.

Then:

1. **Identify inefficiencies**
   - redundant code
   - unnecessary work
   - poor data handling
   - operations that will be slow or memory-heavy on large data

2. **Complexity issues**
   - over-nested logic
   - confusing control flow
   - unneeded abstractions or indirection

3. **Risky assumptions**
   - fragile expectations about inputs
   - poor handling of NA/missing values
   - edge cases likely to break the code

4. **Opportunities to use our preferred stack**
   - places where `data.table`, `collapse`, or `rlang` (in R) would lead to clearer or more efficient code, when appropriate for the project.

5. **Concrete improvements**
   - For each issue:
     - describe the problem
     - propose a specific improvement
     - explain its impact (performance, readability, robustness, maintainability)

End with a short summary:
- Key strengths  
- Key risks  
- Top 3 improvements to implement next  
