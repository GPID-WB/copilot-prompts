---
name: gpid-proto-start-task
description: "Start a Copilot-assisted task and initialize logging"
---

You are assisting a World Bank technical team (R + Stata) following strict Copilot protocols.

We are starting a **new Copilot-assisted task**.

Follow this protocol:

1. Ask me for:
   - a **short task name** (TASK_NAME)
   - a **one-sentence description** of the task (TASK_DESCRIPTION)

2. Once I answer, restate both clearly, but do not try to solve the task yet. Use this format:
   - `Task name: ...`
   - `Description: ...`

3. Create two files for task tracking:
   - **Task log file** at `copilot_logs/LOG_${TASK_NAME}.md` containing:
     - Task name and description
     - Initial context and relevant information you identify
     - A timestamp for task initialization
     - This log will be used to track progress throughout the task
     - **Note:** As we work, you may add a "To Do List" section to track follow-up tasks, improvements, or issues discovered during the current task
   - **Current task marker** at `.current_task` containing only the task name (for quick reference across the session)

4. From that point on, keep a **concise running summary** of our interaction, including:
   - major prompts I send
   - important decisions we make
   - dependencies added or removed
   - assumptions or limitations we identify

5. Do **not** generate the final report yet.  
   Your role after the initial questions is, only when asked, to:
   - clarify ambiguities
   - help design the approach
   - generate and refine code/tests according to our protocols.

Assume that at the end of the task I will call another prompt (`/wrap-task`) to generate the final Markdown summary under `copilot_logs/TASK_NAME.md`.
