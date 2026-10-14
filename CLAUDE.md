# CLAUDE.md

Project conventions for clinic-scheduler, a clinic appointment scheduling app.

## Stack

| Layer | Choice |
|---|---|
| Front end | Latest stable Angular, TypeScript strict mode |
| API | Node + Express + TypeScript |
| Database | PostgreSQL |
| DB access | `pg` with hand-written, parameterized SQL (no ORM) |
| API tests | Vitest with Supertest |
| CI | GitHub Actions (lint and tests on every PR) |

## Repo layout

```
client/        Angular app
server/        Express API
db/
  migrations/  numbered .sql files (001_create_patients.sql, ...)
  seed/        fake data
  queries/     report and practice queries, each with a comment
```

## Conventions

### Angular
- Standalone components, signals, and `inject()`.
- Built-in control flow (`@if`, `@for` with `track`, `@switch`).
- `input()` and `output()` instead of decorators.
- Functional guards and interceptors.
- `OnPush` change detection on every component.
- Typed reactive forms.

### SQL and API
- Every query is parameterized. Never build SQL with string concatenation.
- Enforce rules in the database (constraints, foreign keys, overlap checks), not only in the UI.
- Booking runs inside a transaction.
- Keep the API thin: routes, validation, and SQL.

### Accessibility and tests
- Semantic HTML, labels, keyboard support, and visible focus. Use ARIA only when needed.
- At least one test per component, service, or endpoint.

### Data
- Fake data only. Never use real patient data.

## Workflow

- Each piece of work is a GitHub Issue with acceptance criteria.
- One branch per ticket, named like `feature/12-patient-search` or `fix/15-double-booking`.
- Small, clear commits in the imperative, such as `Add patient search endpoint`.
- Every change goes through a pull request.
- Done means: it works, tests pass, no accessibility issues found with keyboard and axe, and the README is updated if needed.
