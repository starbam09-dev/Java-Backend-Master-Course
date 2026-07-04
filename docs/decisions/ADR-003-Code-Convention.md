# ADR-003: Code Convention

## Status

Accepted

## Context

JBMC will eventually contain Java examples, Spring Boot examples, MyBatis examples, and ERP project code. Code style must be predictable from the beginning.

## Decision

JBMC code examples will use Java 17 as the baseline and follow clear, beginner-readable conventions suitable for textbook publication.

Code exists to teach backend development, not to demonstrate cleverness.

## Principles

- Use Java 17 unless a specific lesson explicitly requires a different version.
- Prefer clear names over abbreviated names.
- Prefer business-domain examples over abstract examples.
- Keep examples aligned with the current lesson.
- Avoid introducing future concepts without explanation.
- Use Gradle for Java and Spring Boot project examples unless explicitly changed by `MASTER_BOOK.md`.

## Consequences

- Code examples should remain readable in Markdown and PDF.
- Style decisions should favor learning clarity.
- Refactoring must not make beginner lessons harder to understand.
- Project code and lesson code should evolve consistently.
