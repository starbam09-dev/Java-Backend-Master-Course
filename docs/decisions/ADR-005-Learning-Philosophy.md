# ADR-005: Learning Philosophy

## Status

Accepted

## Context

Many Java courses teach syntax without connecting it to professional backend work. JBMC must avoid becoming syntax-only material.

## Decision

JBMC teaches Java as a path toward backend ERP development.

Each major concept should be explained through this learning chain:

1. Why the learner needs it
2. How it appears in Spring Boot
3. How it appears in ERP systems

## Principles

- Explain purpose before mechanics.
- Prefer business objects such as `Product`, `Employee`, `Inventory`, `Order`, and `Supplier`.
- Connect beginner topics to later backend usage without overwhelming the learner.
- Treat ERP development as the long-term destination of the course.

## Consequences

- Scanner-only examples should not dominate the course.
- Console examples may be used when helpful, but business-domain examples are preferred.
- Lessons should prepare the learner for later Spring Boot and ERP work.
