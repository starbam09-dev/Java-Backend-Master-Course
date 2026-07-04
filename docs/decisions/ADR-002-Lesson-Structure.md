# ADR-002: Lesson Structure

## Status

Accepted

## Context

JBMC will contain many lessons over a long period. Without a fixed lesson structure, the course will become difficult to review, publish, and maintain.

## Decision

Every lesson must follow the exact section order defined in `MASTER_BOOK.md`.

The lesson structure is fixed to support predictable reading, GitBook conversion, PDF publishing, review, and future maintenance.

## Principles

- Lesson structure is not decided per lesson.
- Every lesson must begin with learning goals and prerequisite knowledge.
- Every lesson must explain why the concept matters before moving into practice.
- Every lesson must connect the topic to Spring Boot and ERP.
- Missions, checklists, interview questions, and review questions are required learning reinforcements.

## Consequences

- Lesson files can be reviewed consistently.
- Publication formatting can rely on a stable section model.
- Future lesson templates must follow `MASTER_BOOK.md`.
- A lesson that does not follow the required order is incomplete.
