---
name: gpid-proto-start-task
description: "Plan and initialize a new Copilot-assisted task"
agent: gpid-planner
---

You are assisting a World Bank technical team (R + Stata) following strict Copilot protocols.

**This is the mandatory first step for every task. Run this before any implementation work.**

---

## Step 1  Gather task information

Ask me for:
- a **short task name** (TASK_NAME, no spaces, use underscores)
- a **description** of the task (TASK_DESCRIPTION)
- whether this task was **assigned by a TTL** (yes/no)

Wait for my answers before continuing.

---

## Step 2  Produce the plan

Once I answer, produce a **numbered checklist plan** for this task. Each step must be:
- Specific enough to be deterministic (another developer could follow it without ambiguity)
- Scoped to a single action or decision
- Written in this strict format:

```
- [ ] Step 1: <action>
- [ ] Step 2: <action>
...
```

The plan must cover these phases in order:
1. **Scoping**  files to read, context to gather, questions to resolve before coding
2. **Design**  decisions to make before writing code (architecture, patterns, interfaces)
3. **Implementation**  specific functions, files, or modules to create or modify
4. **Validation**  tests, checks, and edge cases to verify
5. **Documentation**  comments, Roxygen2, log update
6. **Wrap-up**  final review and `/gpid-proto-wrap-task`

Do **not** start implementing anything yet. Only produce the plan.

---

## Step 3  TTL approval reminder

If the task is TTL-assigned, display this message exactly:

>  **TTL Approval Required**: This task was assigned by a TTL. Please present the plan above to the TTL and obtain approval before proceeding.
> Type `approved` here once confirmed, then continue.

If not TTL-assigned, proceed directly to Step 4.

---

## Step 4  Initialize the task log

Create `copilot_logs/LOG_${TASK_NAME}.md` with this exact structure:

```markdown
# Task: ${TASK_NAME}

**Description:** ${TASK_DESCRIPTION}
**Date:** ${ISO_DATE}
**TTL-assigned:** yes/no
**Plan approved:** yes/not applicable

---

## PLAN

> This plan was established before implementation began.
> Any deviation must be logged with the strict heading:
> `###  PLAN DEVIATION  YYYY-MM-DD HH:MM:SS`

- [ ] Step 1: ...
- [ ] Step 2: ...
...

---

## Plan Deviations

> Updated automatically whenever a plan deviation is logged.
> Each entry corresponds to a `###  PLAN DEVIATION` section below.

*(no deviations recorded yet)*

---

## Update Log

*(updates appended here via `/gpid-proto-log-update`)*
```

Also create `.current_task` containing only the task name.

---

## Step 5  Begin tracking

After saving the log, confirm:
-  Plan saved to `copilot_logs/LOG_${TASK_NAME}.md`
-  `.current_task` created
-  Ready to begin implementation

From this point on, keep a **concise running summary** of the session, including:
- major prompts sent
- important decisions made
- dependencies added or removed
- assumptions or limitations identified

Do **not** generate the final report yet  that happens at `/gpid-proto-wrap-task`.

---

## Deviation rule (active for the entire session)

If at any point the plan needs to change:

1. **Do not proceed silently.** Flag the deviation before implementing it.
2. When logging via `/gpid-proto-log-update`, the heading **must** be:
   ```
   ###  PLAN DEVIATION  YYYY-MM-DD HH:MM:SS
   ```
3. Append a one-sentence summary to the `## Plan Deviations` block at the top of the log.
4. State the rationale for the change clearly.
