---
name: gpid-proto-document-code
description: "Add comments and Roxygen2 documentation for R/Stata code"
---

You will be given one or more functions or scripts, mainly in **R** (often using `data.table`, `collapse`, `rlang`) and sometimes **Stata**.

If it is unclear what code to document, first ask me **which function/file/selection** to use.

Then follow this protocol:

1. **In-code comments**
   - Add clear, human-readable comments that explain:
     - what each major block does
     - why this approach or pattern is appropriate
     - important trade-offs or design decisions
   - Avoid trivial “this line adds 1” comments. Focus on intent.

2. **Roxygen2 (for R functions)**
   - For each relevant R function, add or update:
     - `@title`
     - `@description`
     - `@param`
     - `@return`
     - `@examples` (when helpful and not trivial)
     - `@import` / `@importFrom` only when truly needed.
   - Prefer our usual stack (`data.table`, `collapse`, `rlang`) when appropriate.

3. **Plain-language explanation**
   - At the end, write a short, plain-language explanation of how the main function(s) work, suitable for a teammate reading them for the first time.

Return:
1. The updated code (with comments and Roxygen2 tags).  
2. The plain-language explanation as a separate Markdown section that can be added to the task summary.
