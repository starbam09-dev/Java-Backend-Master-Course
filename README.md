# Java-Backend-Master-Course (JBMC)

Java-Backend-Master-Course, abbreviated as JBMC, is a long-term backend development textbook and knowledge base.

This repository is not a simple Java lecture archive. Its final purpose is to build a publication-ready learning path that trains a developer who can create ERP systems with Java, Spring Boot, MyBatis, Oracle, Git, REST API, JWT, Docker, and Linux.

## Project Principle

`MASTER_BOOK.md` is the highest-priority source of truth in this repository.

Every lesson, example, diagram, project, and document must follow `MASTER_BOOK.md`.

Lesson order must not be changed.
Curriculum structure must not be changed without updating `MASTER_BOOK.md` first.
Each lesson must build on previous lessons.

## Learning Philosophy

JBMC does not teach Java only for Java's sake.

JBMC teaches Java so that the learner can become a backend developer capable of building ERP systems.

Each lesson explains concepts in this order:

1. Why we learn it
2. Where it is used in Spring Boot
3. Where it is used in ERP

Examples should prefer business-oriented objects such as `Book`, `Product`, `Employee`, `Inventory`, `Order`, and `Supplier`.

## Scope

JBMC will eventually include:

- Java textbook content
- Spring Boot textbook content
- MyBatis textbook content
- Oracle textbook content
- Git textbook content
- Docker textbook content
- ERP project material
- IntelliJ practice
- Example code
- UML
- ERD
- Mermaid diagrams
- Markdown sources for PDF generation

## Technology Stack

- Java 17
- IntelliJ IDEA
- Gradle
- Spring Boot
- MyBatis
- Oracle XE 21c
- Git
- GitHub
- Swagger
- JWT
- Docker
- Linux

## Repository Structure

- `lesson/`: Lesson folders from `Lesson01` to `Lesson50`
- `projects/`: Practice projects and final ERP project sources
- `resources/`: Supporting learning resources
- `resources/diagrams/`: Diagram source groups for class, sequence, ERD, flow, and architecture diagrams
- `diagrams/`: UML, ERD, Mermaid, and architecture diagrams
- `images/`: Image assets for GitBook and PDF publication
- `pdf/`: PDF build outputs and PDF-related resources
- `template/`: Lesson and document templates
- `templates/`: Reusable authoring templates
- `prompts/`: Reusable prompts for lesson, mission, review, code review, and refactoring work
- `workspace/`: Phase-oriented authoring workspace
- `docs/`: Project-level documentation system
- `docs/decisions/`: Architecture Decision Records for stable project decisions
- `docs/glossary/`: Shared terminology
- `docs/rules/`: Project rules

## Required Documents

- `MASTER_BOOK.md`: Curriculum authority and lesson order
- `MASTER_INDEX.md`: Repository navigation index
- `ROADMAP.md`: Long-term development roadmap
- `PLANS.md`: Working plans and milestone queue
- `LESSON_STATUS.md`: Lesson production status
- `CHANGELOG.md`: Project history
- `AGENTS.md`: Rules for Codex and future AI-assisted work
- `KnowledgeMap.md`: Mermaid-based learning connection map from Java to ERP
- `docs/decisions/ADR-001-Project-Vision.md`: Project vision decision
- `docs/decisions/ADR-002-Lesson-Structure.md`: Lesson structure decision
- `docs/decisions/ADR-003-Code-Convention.md`: Code convention decision
- `docs/decisions/ADR-004-Repository-Structure.md`: Repository structure decision
- `docs/decisions/ADR-005-Learning-Philosophy.md`: Learning philosophy decision
- `docs/decisions/ADR-006-ERP-Integration.md`: ERP integration decision
- `docs/decisions/ADR-007-Git-Workflow.md`: Git workflow decision
- `docs/decisions/ADR-008-PDF-Publishing.md`: PDF publishing decision
- `docs/glossary/Glossary.md`: Shared terminology
- `docs/rules/RULE-001.md`: `MASTER_BOOK.md` authority rule
- `docs/rules/RULE-002.md`: Lesson structure preservation rule
- `docs/rules/RULE-003.md`: Documentation source and publication rule

## Current Status

The repository foundation and authoring environment have been created.

Lesson writing has not started yet.
