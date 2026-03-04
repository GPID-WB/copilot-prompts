---
name: gpid-guide-log-short-task
description: "Create or update a task progress log for the ongoing chat session"
model: Claude Sonnet 4.5
argument-hint: "TASK_NAME for copilot_logs/LOG_TASK_NAME.md"
---

We are creating or updating a **task progress log** for an ongoing Copilot-assisted chat session.

## Steps

### 1. Resolve `TASK_NAME`

Use the value provided via `argument-hint`. If not provided, ask the user for a short, descriptive name without spaces (use underscores). Example: `premium_advantages`.

### 2. Check for an existing log

Check whether `copilot_logs/LOG_${TASK_NAME}.md` already exists:

- **If it exists**: append a new dated session block — do not overwrite the file.
- **If it does not exist**: create the file with the structure below.

### 3. Write the session block

Each session block should contain:

- **Timestamp**: current date and time in ISO 8601 format (`YYYY-MM-DD HH:MM:SS`)
- **Actions taken**: decisions made, code changes, dependencies added or removed
- **Assumptions & limitations**: notable assumptions or known constraints
- **Challenges**: blockers, issues, or difficulties encountered

### 4. To Do List

- Identify potential follow-up tasks, improvements, technical debt, or issues discovered during the session.
- **Before writing**, present the suggested items to the user in a numbered list.
- Ask: *"I suggest adding these items to the To Do List. Would you like me to include them, or modify/add others?"*
- After confirmation, add or update the `## To Do List` section in the log.
  - Each item should follow the format: `- [ ] <description>` (use `- [x]` for completed items)
  - If the section already exists, preserve completed items and append new ones.
  - If the user declines all suggestions, include an empty `## To Do List` section.

