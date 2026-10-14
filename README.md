# clinic-scheduler

A clinic appointment scheduling app: patients, providers, and appointments, with the database enforcing that a provider can never be double-booked.

Built with a modern Angular front end, a small Express API, and a PostgreSQL database with hand-written SQL.

> All data in this project is fake. No real patient information is used.

## Status

In early development. See the [issues](../../issues) for the current work.

## Tech stack

| Layer | Choice |
|---|---|
| Front end | Angular 22, TypeScript (strict), standalone components, signals |
| API | Node, Express, TypeScript |
| Database | PostgreSQL, accessed with `pg` and parameterized SQL (no ORM) |
| Tests | Angular CLI test runner, Vitest and Supertest for the API |
| CI | GitHub Actions |

## Project structure

```
client/        Angular app
server/        Express API
db/
  migrations/  numbered .sql files that build the schema
  seed/        fake data
  queries/     report queries, each with a comment explaining it
```

## Prerequisites

- Node.js 22 or newer
- PostgreSQL 16 or newer

## Getting started

### Client

```
cd client
npm install
npm start
```

The app runs at http://localhost:4200.

Run the tests with `npm test`.

### API and database

Setup steps for `server/` and `db/` will be added as they are built.

## Decisions I made

This section will be filled in as the project grows.

## Accessibility

Notes from keyboard-only and screen reader testing will be added here.
