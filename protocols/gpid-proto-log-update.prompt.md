---
name: gpid-proto-log-update
description: "Update the task progress log with new information"
model: ['Claude Haiku 4.5', 'Claude Sonnet 4.5']  # lightweight model; update both entries if model is retired
argument-hint: "TASK_NAME for copilot_logs/LOG_TASK_NAME.md"
---

We are updating the **task progress log** for an ongoing Copilot-assisted task.

## Retrieving the task name

Locate the task name you provided at the start of this conversation session. Confirm it by restating:
> Task name: [TASK_NAME]

Then proceed to update `copilot_logs/LOG_${TASK_NAME}.md` where `${TASK_NAME}` is that task name.

**Fallback:** If you cannot locate the task name in the conversation history, read `.current_task` to retrieve it. If that file doesn't exist either, ask the user to provide the task name with a single prompt: `Please provide the TASK_NAME to update copilot_logs/LOG_TASK_NAME.md.`

After confirming the task name, proceed with the update:

## Update the log file `copilot_logs/LOG_${TASK_NAME}.md`:

1. **Open and review** the existing log file to understand its current state and structure.

2. **Append a new update section** with:
   - **Timestamp**: Include the current date and time in ISO format (YYYY-MM-DD HH:MM:SS)
   - **Progress summary**: Key accomplishments since the last update
   - **Challenges encountered**: Any blockers, issues, or difficulties faced
   - **Changes to plan**: Deviations from the original approach or scope
   - **Next steps**: What will be tackled next

3. **Update or create the To Do List section**:
   - Review the conversation since the last log update (or since task initialization)
   - Identify potential follow-up tasks, improvements, technical debt, or issues discovered
   - **Before adding to the log**, present your suggested to-do items to the user in a clear list format
   - Ask: "I suggest adding these items to the To Do List. Would you like me to include them, or would you like to modify/add others?"
   - Only after user confirmation, add/update the "## To Do List" section in the log
   - If a To Do List section already exists, preserve completed items and update with new suggestions

4. **Maintain organization** by:
   - Using clear section headings for each update
   - Keeping entries concise but informative
   - Ensuring the log remains chronologically ordered
   - Using consistent formatting throughout

5. **Preserve all prior content**: Do not remove or modify previous log update entries; only append new information. The `## Plan Deviations` block is the only section near the top of the log that should be modified (to accumulate deviation summaries).

Return the updated `copilot_logs/LOG_${TASK_NAME}.md` file with the new update appended.

