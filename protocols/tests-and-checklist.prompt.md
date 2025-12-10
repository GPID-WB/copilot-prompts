---
name: tests-and-checklist
description: "Generate validation checklist and tests for a function or module"
---

You will help design validation for a function, module, or script.

If it is unclear what to validate, first ask me **which function/file/selection** to focus on.

Then follow this protocol:

1. **Validation checklist**
   - List:
     - expected inputs and outputs
     - required dependencies
     - main assumptions
     - potential failure points
     - edge cases that must be tested

2. **R unit tests (`testthat`)**
   - When the code is in R, generate `testthat` tests that cover:
     - normal cases
     - edge cases
     - wrong input types
     - missing values
     - extreme or unusual data scenarios

3. **Stata tests**
   - When the code is in Stata, generate a do-file with assertions/checks for:
     - realistic data
     - corner cases
     - unexpected or malformed inputs

4. **Performance-sensitive checks (optional)**
   - If the code is performance-critical or uses large data, propose tests that:
     - stress memory usage
     - expose slow operations or unnecessary copies

Return:
- the validation checklist (Markdown)  
- the test code (R `testthat` or Stata do-file) ready to be added to the repository  
