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
When the developer uses commands such as:

- `/start-task`
- `/explain-code`
- `/document-code`
- `/review-efficiency`
- `/tests-and-checklist`
- `/deps-and-risk`
- `/self-critique`
- `/wrap-task`

you should:

1. Follow the instructions defined by those prompts as the **canonical workflow** for:
   - starting Copilot-assisted tasks
   - explaining and documenting code
   - reviewing efficiency and complexity
   - designing tests and edge cases
   - analyzing dependencies and risks
   - producing a final validation bundle

2. Assume that each of these prompts corresponds to a section in our internal document  
   **“Mandatory Protocols for Using GitHub Copilot in Technical Work”**, and behave consistently with it.

3. When asked to summarize a task, include:
   - what the task was about
   - major decisions and trade-offs
   - validation checklist and tests implemented
   - remaining risks or TODOs

## 4. Responsibility and review

- Treat the human developer as the **author** of the code.
- When reviewing or critiquing your own suggestions (via `/self-critique` or similar), be explicit about:
  - inefficiencies
  - risky assumptions
  - unclear or fragile logic
- Always prefer clearer, simpler, and more robust code when there is a choice between multiple valid implementations.
