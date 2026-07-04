# MASTER_BOOK.md

This document is the highest-priority source of truth for Java-Backend-Master-Course (JBMC).

All lessons, examples, diagrams, projects, indexes, plans, and generated publication files must follow this document.

## Project Name

Java-Backend-Master-Course (JBMC)

## Final Goal

Build a publication-ready backend development textbook and knowledge base that guides a learner from Java fundamentals to ERP system development.

JBMC must cover:

- Java object-oriented programming
- Spring Boot
- MyBatis
- Oracle
- Git
- REST API
- JWT
- Docker
- Linux
- ERP project development

## Core Rule

`MASTER_BOOK.md` has the highest priority.

All lessons must be written based on this document.

Lesson order must never be changed.

The curriculum must not be modified arbitrarily.

Each lesson must build on previous lessons.

## Teaching Philosophy

This course does not teach Java as an isolated language.

This course teaches Java to create backend developers who can build ERP systems.

Every lesson should explain:

1. Why the concept is learned
2. Where the concept is used in Spring Boot
3. Where the concept is used in ERP

Prefer business-domain examples over simple console-only examples.

Recommended domain objects:

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

## Required Lesson Structure

Every lesson must use the following order exactly:

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

## Fixed Curriculum

### Phase 1: Java Recovery

- Lesson01
- Lesson02
- Lesson03
- Lesson04
- Lesson05
- Lesson06
- Lesson07
- Lesson08
- Lesson09
- Lesson10

### Phase 2: OOP

- Lesson11
- Lesson12
- Lesson13
- Lesson14
- Lesson15
- Lesson16
- Lesson17
- Lesson18
- Lesson19
- Lesson20

### Phase 3: Collection

- Lesson21
- Lesson22
- Lesson23
- Lesson24
- Lesson25
- Lesson26
- Lesson27
- Lesson28
- Lesson29
- Lesson30

### Phase 4: Spring Boot

- Lesson31
- Lesson32
- Lesson33
- Lesson34
- Lesson35
- Lesson36
- Lesson37
- Lesson38
- Lesson39
- Lesson40

### Phase 5: ERP

- Lesson41
- Lesson42
- Lesson43
- Lesson44
- Lesson45
- Lesson46
- Lesson47
- Lesson48
- Lesson49
- Lesson50

## Repository Requirements

Required root files:

- `README.md`
- `AGENTS.md`
- `MASTER_BOOK.md`
- `MASTER_INDEX.md`
- `ROADMAP.md`
- `PLANS.md`
- `LESSON_STATUS.md`
- `CHANGELOG.md`
- `LICENSE`
- `.gitignore`

Required root folders:

- `lesson/`
- `projects/`
- `resources/`
- `diagrams/`
- `images/`
- `pdf/`
- `template/`

The `lesson/` folder must contain placeholder folders from `Lesson01` to `Lesson50`.

## Publication Rule

Markdown is the source of truth.

PDF output must be generated from Markdown.

Markdown should remain compatible with GitBook and PDF publication workflows.

## Current Work Boundary

The current repository foundation creates structure and planning documents only.

No lesson body, including Lesson01, is created in this foundation step.
