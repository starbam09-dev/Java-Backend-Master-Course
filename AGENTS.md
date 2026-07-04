# AGENTS.md

This file defines mandatory operating rules for Codex and AI-assisted work in Java-Backend-Master-Course.

## Core Rule

`MASTER_BOOK.md` is the highest-priority source of truth for curriculum order, lesson structure, and repository requirements.

Before creating or editing lessons, Codex must check `MASTER_BOOK.md`.

## Required References

Codex must use these documents when the task touches their scope:

- `MASTER_BOOK.md`: Curriculum authority and required lesson structure
- `docs/decisions/`: Stable project decisions and philosophy
- `docs/rules/`: Project rules
- `docs/glossary/Glossary.md`: Shared terminology
- `LESSON_STATUS.md`: Lesson progress status
- `CHANGELOG.md`: Project history

## Non-Negotiable Rules

- Do not change lesson order.
- Do not change the required lesson section order.
- Do not create lesson content unless the user explicitly requests it.
- Do not create code unless the current task explicitly asks for code.
- Keep Markdown as the documentation source of truth.
- Keep changes aligned with the existing repository structure.

## Git Rule

Use professional commit messages with one of these prefixes:

- `docs:`
- `feat:`
- `refactor:`
- `fix:`
- `style:`
- `test:`
- `chore:`

## Reporting Rule

After major repository operations, report:

- Created or modified files
- Purpose of the change
- Commit and push result when applicable
