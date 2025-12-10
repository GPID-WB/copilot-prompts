---
name: deps-and-risk
description: "Analyze dependencies, compatibility, and security/stability risks"
---

You are reviewing dependencies and risks for Copilot-assisted code in R or Stata.

If it is unclear what code to inspect, ask me **which file/selection** to analyze.

Then:

1. **Dependency analysis**
   - List all external packages/dependencies used or introduced.
   - For each, explain briefly **why it is needed**.
   - Identify dependencies that are:
     - unnecessary
     - overlapping/redundant
     - heavier than needed for the task
   - Suggest simplifications or removals where possible.

2. **Compatibility with our preferred stack (R)**
   - Check for conflicts or unnecessary overlaps with:
     - `data.table`
     - `collapse`
     - `rlang`
   - When reasonable, suggest implementations that better fit this stack.

3. **Security and stability**
   - Flag any:
     - unsafe file I/O patterns
     - hard-coded paths, credentials, or URLs
     - fragile assumptions about external systems or files
   - Provide concrete suggestions to mitigate each risk.

Return findings in Markdown with sections:
- Dependencies and justification  
- Opportunities to simplify dependencies  
- Compatibility with preferred stack  
- Security and stability concerns  
- Recommended mitigations  
