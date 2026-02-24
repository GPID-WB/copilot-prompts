---
name: gpid-proto-explain-code
description: "Explain code step-by-step and surface assumptions"
model: ['Claude Haiku 4.5', 'Claude Sonnet 4.5']  # lightweight model; update both entries if model is retired
---

You will be asked to explain a function, test file, or script (usually R or Stata).

If the context is ambiguous, first ask me **what code or file you should focus on** (e.g., current selection, specific function, or file).

Then follow this protocol:

1. **High-level overview**
   - In 3–5 sentences, explain what the code does conceptually.

2. **Step-by-step explanation**
   - Walk through the major blocks of the code.
   - Focus on logic and structure rather than line-by-line commentary.

3. **Assumptions**
   - Explicitly list assumptions about:
     - input types, shapes, and ranges
     - required columns / variables
     - expected data structure (e.g., data.table, Stata dataset)
     - external dependencies or files

4. **Failure points**
   - Identify where the code might break or behave incorrectly:
     - missing or malformed inputs
     - edge cases (empty data, small N, extreme values)
     - performance pitfalls on large data

Return your explanation in **clean Markdown** with headings:

- High-level overview  
- Step-by-step explanation  
- Assumptions  
- Potential failure points  

This text should be ready to paste into the task summary.

