# ADR-007: Git Workflow

## Status

Accepted

## Context

JBMC is a long-term repository. Git history must remain useful for tracking curriculum growth, documentation changes, and future project code.

## Decision

JBMC will use professional commit messages from the beginning.

Allowed commit prefixes are:

- `docs:`
- `feat:`
- `refactor:`
- `fix:`
- `style:`
- `test:`
- `chore:`

## Principles

- Commits should describe one coherent change.
- Documentation changes should usually use `docs:`.
- Generated outputs should not obscure source changes.
- Markdown source files are more important than generated publication files.

## Consequences

- Commit history should remain readable as the project grows.
- Large unrelated changes should be split.
- Changes to rules, ADRs, and curriculum authority documents should be easy to find.
