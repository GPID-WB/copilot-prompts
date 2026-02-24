```instructions
# Copilot Instructions for This Repository

This repository belongs to the GPID technical team.  
We follow **mandatory protocols** when using GitHub Copilot for technical work.

## 1. General behavior

- Treat Copilot as an assistant, not a replacement for engineering judgment.
- Prefer our core stack in R: `data.table`, `collapse`, `rlang`, and base R where appropriate.
- Avoid unnecessary dependencies and over-complicated patterns.
- Always assume that code will be maintained by other teammates.

## 2. Context and understanding the project

When helping with tasks in this repository:

- Use the full project context when appropriate (e.g., `@workspace` or equivalent).
- Prefer to reuse existing patterns, style, and conventions already present in the codebase.
- Before generating large changes, briefly summarize your understanding of the task and ask for confirmation when needed.

## 3. Mandatory protocols and prompt files

We use a shared set of **Copilot user prompt files** that implement our protocols.

### 3.1 How every task must start

**Every task must begin by selecting the GPID Planner custom agent from the agents dropdown in GitHub Copilot Chat.**  
This is the mandatory first step — not a slash command. The GPID Planner agent is read-only and produces a deterministic, approved plan before any code is written.

Once the plan is confirmed, use the "Start Implementation" handoff button to switch to the standard implementation agent.

### 3.2 Canonical workflow

1. Select **GPID Planner** agent → run `/gpid-proto-start-task` (plan + initialize)
2. Implement using the prompts below
3. Run `/gpid-proto-log-update` after each meaningful milestone
4. Run `/gpid-proto-wrap-task` to close the task

### 3.3 Protocol prompt commands

When the developer uses commands such as:

- `/gpid-proto-start-task` ← **mandatory first step for every task** (plan + initialize)
- `/gpid-proto-log-update`
- `/gpid-proto-explain-code`
- `/gpid-proto-document-code`
- `/gpid-proto-review-code`
- `/gpid-proto-tests-checklist`
- `/gpid-proto-deps-risk`
- `/gpid-proto-wrap-task`

you should:

1. Follow the instructions defined by those prompts as the **canonical workflow** for:
   - **planning and initializing tasks before implementation begins** (`/gpid-proto-start-task` inside GPID Planner — always first)
   - logging milestones and tracking plan deviations
   - explaining and documenting code
   - reviewing efficiency, complexity, and robustness
   - designing tests and edge cases
   - analyzing dependencies and risks
   - producing a final validation bundle

   `/gpid-proto-start-task` must be run inside the GPID Planner agent on every task, without exception. It produces the deterministic step-by-step plan, handles TTL approval reminders, and initializes the log with the `## PLAN` section and the `## Plan Deviations` tracking block.

2. Assume that each of these prompts corresponds to a section in our internal document  
   **"Mandatory Protocols for Using GitHub Copilot in Technical Work"**, and behave consistently with it.

3. When asked to summarize a task, include:
   - what the task was about
   - major decisions and trade-offs
   - validation checklist and tests implemented
   - remaining risks or TODOs

### 3.4 Plan deviations

If the implementation deviates from the approved plan, the deviation must be logged using `/gpid-proto-log-update` with the strict marker:

```
### ⚠️ PLAN DEVIATION — YYYY-MM-DD HH:MM:SS
```

Every deviation is also appended to the `## Plan Deviations` summary block at the top of the task log. This block is greppable: `git grep "PLAN DEVIATION" copilot_logs/` surfaces all deviations across all tasks.

## 4. Responsibility and review

- Treat the human developer as the **author** of the code.
- When reviewing or critiquing your own suggestions (via `/gpid-proto-review-code` or similar), be explicit about:
  - inefficiencies
  - risky assumptions
  - unclear or fragile logic
- Always prefer clearer, simpler, and more robust code when there is a choice between multiple valid implementations.

```
