<!-- 
SYNC IMPACT REPORT
Version change: null -> 1.0.0
Modified principles:
  - [PRINCIPLE_1_NAME] -> I. Strict Dependency Management (The pom.xml Rule)
  - [PRINCIPLE_2_NAME] -> II. Test-First Development (Strict TDD)
  - [PRINCIPLE_3_NAME] -> III. Exhaustive Integration Testing
  - [PRINCIPLE_4_NAME] -> IV. Uncompromising Clean Code
  - [PRINCIPLE_5_NAME] -> V. Strict Module Layering
Added sections: 
  - Technology Stack & Constraints
  - Development Workflow & Approvals
Templates updated:
  - .specify/templates/tasks-template.md (✅ updated)
  - .gemini/commands/speckit.tasks.toml (✅ updated)
Follow-up TODOs: None
-->

# Contratto MVP Constitution

## Core Principles

### I. Strict Dependency Management (The pom.xml Rule)
I (the AI) am strictly forbidden from modifying the pom.xml file. Whenever a new dependency is required to fulfill a feature, I must halt and explicitly ask the user to manually add it to their pom.xml. I must ask the user to specify the exact version of the library they wish to use; I will not assume or hallucinate versions.

### II. Test-First Development (Strict TDD)
Test-Driven Development is non-negotiable. The workflow must always be: Write the failing unit/integration test first. Present the test to the user. Wait for the user to confirm the test fails in their environment. Only after confirmation, implement the minimum required feature code to make the test pass. Refactor if necessary, then run the tests again.

### III. Exhaustive Integration Testing
Every connection, API endpoint, and cross-module event must be tested with every possible edge case. There are no exceptions for "simple" connections. Happy paths, error states, null inputs, and boundary limits must all have dedicated integration test coverage.

### IV. Uncompromising Clean Code
Every line of code must adhere to the highest standards of Clean Code.
- **YAGNI (You Aren't Gonna Need It)**: Do not over-engineer or write speculative code for future features. Implement exactly what the current test demands.
- **DRY (Don't Repeat Yourself)**: Extract reusable logic immediately; do not duplicate code blocks.
- **Code must be self-documenting** with clear, domain-driven naming conventions.

### V. Strict Module Layering
Every module (iam, account, catalog, booking, billing, communication, reputation) must strictly isolate its concerns using the following unidirectional data flow:
**DTO -> Controller -> Service -> Repository -> Model -> ORM -> DB**
Controllers only speak to Services via DTOs. Services handle business logic and interact with Repositories. Repositories map Models to ORM entities. Layers cannot be bypassed (e.g., a Controller cannot call a Repository directly).

## Technology Stack & Constraints

- **Language**: Java 21
- **Framework**: Spring Boot 4.0.3
- **Third-Party Libraries**: All versions must be explicitly defined and provided by the user. I will not assume library versions.
- **Build Tool**: Maven (Modifications strictly handled by the user).

## Development Workflow & Approvals

- **Step-by-Step Execution**: I will not write a massive block of files all at once. I will tackle one layer or one test at a time.
- **Explicit Approval**: Every single implementation step (a test written, a service created, a controller mapped) requires explicit approval from the user before I move on to the next step.
- **Self-Review Gate**: Before outputting any code, I will internally review it against this Constitution to ensure it matches the layered architecture, adheres to DRY/YAGNI, and follows the test-driven flow.

## Governance

This Constitution supersedes all other general programming advice or standard AI behaviors. I must review every piece of code written against these rules. If a request from the user accidentally violates these rules (e.g., asking to skip a test), I must gently remind the user of the Constitution and ask if they wish to amend the rules or proceed with TDD.

**Version**: 1.0.0 | **Ratified**: 2026-04-30 | **Last Amended**: 2026-04-30
