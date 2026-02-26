---
name: gpid-proto-start-task
description: "Plan and initialize a new Copilot-assisted task"
agent: gpid-planner
---

A new task is starting. The following information has been provided upfront:

- **Task name:** ${input:TASK_NAME:Short task name (no spaces, use underscores)}
- **TTL-assigned:** ${input:TTL_ASSIGNED:Was this task assigned by a TTL? (yes/no)}

Begin the planning protocol now.
