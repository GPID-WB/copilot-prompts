---
name: gpid-proto-wrap-task
description: "Create the final task summary and validation bundle"
argument-hint: "TASK_NAME for copilot_logs/TASK_NAME.md"
---

We have reached the end of a Copilot-assisted task.

## Retrieving the task name

Locate the task name you provided at the start of this conversation session. Confirm it by restating:
> Task name: [TASK_NAME]

Then proceed to work with `copilot_logs/TASK_NAME.md` and `copilot_logs/LOG_${TASK_NAME}.md` where `${TASK_NAME}` is that task name.

**Fallback:** If you cannot locate the task name in the conversation history, read `.current_task` to retrieve it. If that file doesn't exist either, ask the user to provide the task name with a single prompt: `Please provide a short TASK_NAME to save the final report as copilot_logs/TASK_NAME.md.`

After confirming the task name, proceed with the task completion:

## Step 1: Review the task log

Before generating the final summary, carefully review the existing task log file at `copilot_logs/LOG_${TASK_NAME}.md`. This file contains:
- The task initialization details
- All progress updates recorded throughout the task
- Challenges encountered and solutions implemented
- Changes made to the original plan

Use this log to ensure that all relevant information, decisions, and important details are captured in the final summary. Verify that no critical information is overlooked.

## Step 2: Generate the final Markdown report

Using our full conversation, your running summary, and the reviewed task log, generate a **Markdown report** suitable for saving as `copilot_logs/TASK_NAME.md`. This final report should synthesize all work completed and provide clear documentation for future reference.

Include:

1. **Executive Summary**
   - brief overview of what the task accomplished
   - primary goals achieved
   - overall status (complete, in-progress, blocked, etc.)

2. **Task Overview**
   - what the task was about
   - main files/functions affected
   - major decisions and trade-offs made

3. **Technical Explanation**
   - step-by-step description of how the code works
   - important algorithmic or design choices
   - any performance considerations
   - rationale for technical decisions

4. **Plain-Language Overview**
   - why the code exists
   - how a teammate should use it
   - non-technical explanation of the behavior

5. **Documentation and Comments**
   - confirmation of in-code comments and Roxygen2 docs (for R)
   - any important notes for future maintainers
   - known limitations or caveats

6. **Validation and Testing**
   - validation checklist with status for each item
   - unit tests and edge cases covered (summarize what is tested)
   - error-handling strategy (how invalid or unexpected inputs are handled)
   - performance-sensitive tests, if applicable

7. **Dependencies and Risk Analysis**
   - summary of dependency decisions
   - key security/stability considerations
   - any external factors that could affect the work

8. **Self-Critique and Follow-Ups**
   - main issues uncovered by reviews/self-critique
   - remaining TODOs or recommended future improvements
   - potential enhancements or optimizations for next iteration
   - **To Do List**: Extract any to-do items from the task log (`copilot_logs/LOG_${TASK_NAME}.md`)
     - Before finalizing, present the compiled to-do list to the user
     - Ask: "Here are the to-do items identified during this task. Would you like to add, remove, or modify any items before I include them in the final report?"
     - Wait for user confirmation or modifications before proceeding

Return **only** the Markdown document, and save it as `copilot_logs/${input}.md`.

This final report, combined with the task log (`copilot_logs/LOG_${input}.md`), provides a complete record of the task work and can serve as reference material for future similar tasks.

## Step 3: Clean up temporary files

After creating `copilot_logs/TASK_NAME.md`, ask the user: **"May I delete the temporary `.current_task` marker file to keep the project clean?"**

If the user agrees (or does not object), delete `.current_task`. If they prefer to keep it or it doesn't exist, proceed without action.
