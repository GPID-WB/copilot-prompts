---
name: gpid-proto-wrap-task
description: "Create the final task summary and validation bundle"
argument-hint: "TASK_NAME for copilot_logs/TASK_NAME.md"
---

We have reached the end of a Copilot-assisted task.

The task name is: **${input}**  
Use this as `TASK_NAME` (for example in `copilot_logs/${input}.md`).

If `${input}` is not provided or is empty, follow this fallback logic:

- If a `TASK_NAME` was provided earlier in the conversation, reuse that value and confirm it by restating: `Task name: ...`.
- If no prior `TASK_NAME` can be found, ask the user to provide a short task name with a single prompt: `Please provide a short TASK_NAME to save the final report as copilot_logs/TASK_NAME.md.`

After confirming or obtaining a valid `TASK_NAME`, proceed to generate the Markdown report described below, and save it as `copilot_logs/TASK_NAME.md`.

Using our full conversation and your running summary, generate a **Markdown report** suitable for saving as `copilot_logs/TASK_NAME.md`. Include:

1. **Task overview**
   - what the task was about
   - main files/functions affected
   - major decisions and trade-offs

2. **Technical explanation**
   - step-by-step description of how the code works
   - important algorithmic or design choices
   - any performance considerations

3. **Plain-language overview**
   - why the code exists
   - how a teammate should use it
   - non-technical explanation of the behavior

4. **Documentation and comments**
   - confirmation of in-code comments and Roxygen2 docs (for R)
   - any important notes for future maintainers

5. **Validation bundle**
   - validation checklist
   - unit tests and edge cases (summarize what is covered)
   - error-handling strategy (how invalid or unexpected inputs are handled)
   - performance-sensitive tests, if applicable

6. **Dependencies and risk analysis**
   - summary of dependency decisions
   - key security/stability considerations

7. **Self-critique and follow-ups**
   - main issues uncovered by reviews/self-critique
   - remaining TODOs or recommended future improvements

Return **only** the Markdown document, and save it as `copilot_logs/${input}.md`.
