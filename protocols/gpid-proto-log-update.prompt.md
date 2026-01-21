---
name: gpid-proto-log-update
description: "Update the task progress log with new information"
argument-hint: "TASK_NAME for copilot_logs/LOG_TASK_NAME.md"
---

We are updating the **task progress log** for an ongoing Copilot-assisted task.

The task name is: **${input}**  
Use this as `TASK_NAME` (for example in `copilot_logs/LOG_${input}.md`).

If `${input}` is not provided or is empty, follow this fallback logic:

- If a `TASK_NAME` was established earlier in the conversation, reuse that value and confirm it by restating: `Task name: ...`.
- If no prior `TASK_NAME` can be found, ask the user to provide the short task name with a single prompt: `Please provide the TASK_NAME to update copilot_logs/LOG_TASK_NAME.md.`

After confirming or obtaining a valid `TASK_NAME`, proceed with the update:

## Update the log file `copilot_logs/LOG_${TASK_NAME}.md`:

1. **Open and review** the existing log file to understand its current state and structure.

2. **Append a new update section** with:
   - **Timestamp**: Include the current date and time in ISO format (YYYY-MM-DD HH:MM:SS)
   - **Progress summary**: Key accomplishments since the last update
   - **Challenges encountered**: Any blockers, issues, or difficulties faced
   - **Changes to plan**: Deviations from the original approach or scope
   - **Next steps**: What will be tackled next

3. **Maintain organization** by:
   - Using clear section headings for each update
   - Keeping entries concise but informative
   - Ensuring the log remains chronologically ordered
   - Using consistent formatting throughout

4. **Preserve all prior content**: Do not remove or modify previous updates; only append new information.

Return the updated `copilot_logs/LOG_${TASK_NAME}.md` file with the new update appended.
