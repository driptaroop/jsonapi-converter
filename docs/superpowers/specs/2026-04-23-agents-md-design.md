# AGENTS.md Design

## Goal

Create a repo-specific `AGENTS.md` for AI coding agents working in `jsonapi-converter`.
The document should be concise, code-focused, and operational rather than policy-heavy.

## Audience

Primary audience: AI coding agents.

Secondary audience: humans reading agent guidance, but the document should optimize for machine-executable repo conventions rather than contributor onboarding.

## Constraints

- Keep the document balanced rather than strict.
- Keep it code-focused; do not require README updates for public-facing changes.
- Do not restate generic platform behavior that is not specific to this repository.
- Do not require preservation of Java 7 compatibility. Agents may assume the effective target runtime is Java 17+ unless the task says otherwise.

## Repo Context

- This repository is a Maven Java library, not an application.
- Main library code lives in `src/main/java/com/github/jasminb/jsonapi`.
- Tests live in `src/test/java/com/github/jasminb/jsonapi`.
- JSON fixtures and sample payloads live in `src/test/resources`.
- Build and release configuration live in `pom.xml`.
- The highest-impact code paths are shared conversion surfaces such as `ResourceConverter`, annotations, serialization and deserialization features, relationship handling, and ID handling.

## Proposed AGENTS.md Structure

### 1. Purpose

State that the repository is a JSON:API conversion library and that agents should prefer minimal, well-scoped changes, especially around shared library behavior.

### 2. Repo Map

Document the main code locations:

- `src/main/java/com/github/jasminb/jsonapi` for production code
- `src/test/java/com/github/jasminb/jsonapi` for JUnit 4 tests
- `src/test/resources` for fixture payloads
- `pom.xml` for dependencies, compiler settings, and release profile

### 3. Working Rules

Document the most useful repo-specific guidance:

- Prefer focused edits over broad refactors.
- Treat shared conversion behavior as high impact.
- Add or update regression tests when changing serialization, deserialization, annotations, relationship resolution, or ID handling.
- Keep new fixtures small and scenario-specific.
- Do not use the Maven `release` profile unless the task is explicitly about publishing.

### 4. Verification

Document a simple verification workflow:

- Use `mvn test -Dtest=ClassName` for fast iteration.
- Use `mvn test` as the default full verification command.
- Run broader verification when changes touch shared conversion paths.

## Tone

- Keep the final `AGENTS.md` compact, roughly 30 to 50 lines.
- Use a few hard requirements only where mistakes are expensive.
- Keep the rest as practical guidance.

## Acceptance Criteria

The generated `AGENTS.md` should:

- Be clearly specific to this repository
- Help an agent find the right code and tests quickly
- Call out high-risk library surfaces
- Provide concrete Maven verification commands
- Avoid unnecessary process language
- Stay concise

## Out of Scope

- Release instructions beyond warning against accidental use of the `release` profile
- Human contributor onboarding
- Documentation maintenance policy
- Generic coding-agent rules that are already supplied elsewhere
