# AGENTS.md

This file defines mandatory rules for Codex and any AI-assisted work in the Java-Backend-Master-Course repository.

## Highest Priority Rule

`MASTER_BOOK.md` is the highest-priority document in this repository.

Before creating, editing, moving, or renaming any lesson, Codex must check `MASTER_BOOK.md`.

No lesson order may be changed unless the user explicitly requests a curriculum revision and `MASTER_BOOK.md` is updated first.

## Project Identity

This repository is a long-term textbook and knowledge base for backend development.

The final goal is to create a publication-ready course that teaches:

- Java
- Object-oriented programming
- Spring Boot
- MyBatis
- Oracle
- Git
- REST API
- JWT
- Docker
- Linux
- ERP project development

## Lesson Structure Rule

Every lesson must use the following section order exactly:

1. 학습 목표
2. 선수지식
3. 왜 배우는가
4. 핵심 개념
5. IntelliJ 실습
6. 예제 코드
7. 코드 설명
8. Spring Boot 연결
9. ERP 연결
10. 미션
11. 체크리스트
12. 면접 질문
13. 복습 문제
14. 다음 Lesson

Do not rename, reorder, remove, or add required top-level lesson sections unless the user explicitly changes the standard.

## Curriculum Rule

The fixed lesson phases are:

- Phase 1: Java Recovery, Lesson01 to Lesson10
- Phase 2: OOP, Lesson11 to Lesson20
- Phase 3: Collection, Lesson21 to Lesson30
- Phase 4: Spring Boot, Lesson31 to Lesson40
- Phase 5: ERP, Lesson41 to Lesson50

Codex must preserve this sequence.

## Teaching Philosophy

Every explanation should follow this teaching path:

1. Why the learner needs the concept
2. How the concept appears in Spring Boot
3. How the concept appears in ERP systems

Prefer business-domain examples over abstract console examples.

Recommended domain examples:

- `Book`
- `Product`
- `Employee`
- `Inventory`
- `Order`
- `Supplier`
- `Customer`
- `Department`
- `Invoice`
- `Payment`

## Documentation Rules

Markdown is the source of truth.

PDF files must be generated from Markdown sources.

Markdown must be written so that it can later be used for GitBook and PDF publication.

## Code Rules

Do not create code unless the current task explicitly asks for code.

When code is requested:

- Use Java 17 unless another version is explicitly required.
- Prefer Gradle for Java and Spring Boot projects.
- Keep examples aligned with the current lesson.
- Do not introduce concepts from future lessons without a short note or a forward reference.

## Git Rules

Use professional commit messages from the first commit.

Allowed commit prefixes:

- `docs:`
- `feat:`
- `refactor:`
- `fix:`
- `style:`
- `test:`
- `chore:`

## Change Discipline

Codex must:

- Keep repository structure consistent.
- Avoid unrelated refactoring.
- Avoid renaming files or folders without explicit user approval.
- Update status documents when lesson or project progress changes.
- Report created or modified files clearly after each major repository operation.

## Current Foundation Rule

Lesson folders `Lesson01` through `Lesson50` exist as placeholders only.

Do not write `Lesson01` or any lesson body until the user explicitly requests lesson creation.
