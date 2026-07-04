# ADR-004: Repository Structure

## Status

Accepted

## Context

JBMC will grow into a repository with many Markdown files, diagrams, images, PDF assets, and Java projects.

The structure must remain stable so that future work does not scatter related material.

## Decision

The repository will use a fixed top-level structure defined by `MASTER_BOOK.md`.

The `docs/` directory will contain project-level documentation that supports curriculum decisions, terminology, and rules.

## Structure

- `lesson/`: Lesson folders from `Lesson01` to `Lesson50`
- `projects/`: Practice projects and ERP project sources
- `resources/`: Supporting learning resources
- `diagrams/`: UML, ERD, Mermaid, and architecture diagrams
- `images/`: Image assets for GitBook and PDF publication
- `pdf/`: PDF outputs and PDF-related resources
- `template/`: Reusable document templates
- `docs/decisions/`: Architecture Decision Records
- `docs/glossary/`: Shared terminology
- `docs/rules/`: Project rules

## Consequences

- New root folders require a clear reason and should be reflected in `MASTER_BOOK.md`.
- Long-lived project rules belong in `docs/rules/`.
- Stable project decisions belong in `docs/decisions/`.
- Shared vocabulary belongs in `docs/glossary/`.
