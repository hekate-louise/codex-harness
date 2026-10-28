---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save it in the project as `docs/handoff-NN.md`, where NN is the next number after the existing files (`ls docs/handoff-*.md`; start at 01).

Write only the current state and the next steps. Do not restate working rules: they live in `AGENTS.md`. If a new lasting rule came up in this conversation, do not put it in the handoff; ask the user whether to add one line to `AGENTS.md` instead.

Do not duplicate content already captured in other artifacts (`PLAN.md`, `REQUIREMENTS.md`, `DECISIONS.md`, specs, commits, diffs). Reference them by path instead. Do not copy values that a command can show (the next decision number, line numbers); name the command or the function instead.

Name only the one or two skills the next session should call first, if any.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
