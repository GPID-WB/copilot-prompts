---
name: gpid-proto-plan-task
description: "Plan a Copilot-assisted task before starting implementation"
agent: plan
---

You are assisting a World Bank technical team (R + Stata) following strict Copilot protocols.

**This is Protocol 0 — it must be run before any other protocol, including `/gpid-proto-start-task`.**

## Step 1 — Gather task information

Ask me for:
- a **short task name** (TASK_NAME, no spaces, use underscores)
- a **one-sentence description** of the task (TASK_DESCRIPTION)
- whether this task was **assigned by a TTL** (yes/no)

Wait for my answers before continuing.

## Step 2 — Produce the plan

Once I answer, produce a **numbered checklist plan** for this task. Each step must be:
- Specific enough to be deterministic (i.e., another developer could follow it without ambiguity)
- Scoped to a single action or decision
- Written as a checklist item in this strict format:

```
- [ ] Step 1: <action>
- [ ] Step 2: <action>
...
```

The plan must cover:
1. Understanding and scoping the task (files to read, context to gather)
2. Design decisions to be made before writing code
3. Implementation steps (specific functions, files, or modules to create/modify)
4. Validation steps (tests, checks, edge cases to verify)
5. Documentation steps (comments, Roxygen2, log update)
6. Wrap-up steps (final review, wrap-task)

Do not start implementing anything yet. Only produce the plan.

## Step 3 — TTL approval reminder

If the task is TTL-assigned, display this message exactly:

> ⚠️ **TTL Approval Required**: This task was assigned by a TTL. Please present the plan above to the TTL and obtain approval before proceeding to `/gpid-proto-start-task`.
> Once approved, confirm here and then continue.

If the task is not TTL-assigned, proceed directly to Step 4.

## Step 4 — Save the plan to the log

Create the file `copilot_logs/LOG_${TASK_NAME}.md` with this exact structure:

```markdown
# Task: ${TASK_NAME}

**Description:** ${TASK_DESCRIPTION}  
**Date:** ${ISO_DATE}  
**TTL-assigned:** yes/no  
**Plan approved:** yes/not applicable  

---

## PLAN

> This plan was established before implementation began.  
> Any deviation from this plan must be logged using the strict format:  
> `### ⚠️ PLAN DEVIATION — YYYY-MM-DD HH:MM:SS`

- [ ] Step 1: ...
- [ ] Step 2: ...
...

---

## Plan Deviations

> This section is updated automatically whenever a plan deviation is logged.  
> Each entry below corresponds to a `### ⚠️ PLAN DEVIATION` section in the update log.

*(no deviations recorded yet)*

---

## Update Log

*(updates will be appended here via `/gpid-proto-log-update`)*
```

Also create the file `.current_task` containing only the task name.

## Step 5 — Confirm and hand off

After saving the log, confirm:
- The plan has been saved to `copilot_logs/LOG_${TASK_NAME}.md`
- The `.current_task` file has been created
- The next step is to run `/gpid-proto-start-task`

## Deviation rule (active for the entire session)

From this point on, if at any point during implementation you or I decide to deviate from the plan above:

1. **Do not proceed silently.** Flag the deviation explicitly before implementing it.
2. When logging via `/gpid-proto-log-update`, the update section heading **must** use this strict format:
   ```
   ### ⚠️ PLAN DEVIATION — YYYY-MM-DD HH:MM:SS
   ```
3. The deviation entry must also be appended to the `## Plan Deviations` summary block at the top of the log.
4. Provide the rationale for the deviation clearly.
