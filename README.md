# PMW-Website-Redesign

Website redesign for Peterson Mobile Woodworking. React + Vite + TypeScript frontend and Express + TypeScript backend, built by the SuperSeniors team.

## Repo layout

| Folder    | What it is                                        |
| --------- | ------------------------------------------------- |
| `client/` | React + Vite + TypeScript frontend (Vitest + RTL) |
| `server/` | Express + TypeScript API (Vitest + Supertest)     |
| `.github` | CI workflow and pull request template             |

The repo is an npm workspace, so a single `npm install` at the root installs everything.

## Getting started

Requires Node 22 or newer (see `.nvmrc`).

```sh
npm install
npm run dev:server   # API on http://localhost:3000
npm run dev:client   # site on http://localhost:5173 (proxies /api to the server)
```

## Scripts (run from the repo root)

| Command                | What it does                               |
| ---------------------- | ------------------------------------------ |
| `npm run lint`         | ESLint over client and server              |
| `npm run lint:fix`     | ESLint with auto-fix                       |
| `npm run format`       | Format every file with Prettier            |
| `npm run format:check` | Fail if any file is not Prettier-formatted |
| `npm run typecheck`    | TypeScript type check for both workspaces  |
| `npm test`             | Unit tests for both workspaces             |
| `npm run build`        | Production build of client and server      |

To run a script in one workspace only: `npm test -w client`, `npm run dev -w server`, etc.

## Workflow

`main` is protected. Nobody, including admins, can push to it directly.

1. Create a branch from `main` named after the Jira key, e.g. `PMW-12-contact-form`.
2. Commit, push, and open a pull request. Fill in the PR template, including the Jira key.
3. CI runs ESLint, Prettier and the unit tests (plus typecheck and build). Every check must pass.
4. At least one teammate must approve. Pushing new commits dismisses earlier approvals.
5. Squash and merge once it's approved and green.

Before pushing, run `npm run lint && npm run format:check && npm test` to catch what CI will catch.
