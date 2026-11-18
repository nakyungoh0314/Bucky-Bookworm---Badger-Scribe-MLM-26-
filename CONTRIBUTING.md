# Contributing to Badger Scribe

Keep `main` clean: every change lands by pull request, stays small, and is easy to review.

## Branch naming

Use one branch per PR:

- `person/scope-short-summary` (example: `alex/search-filters-api`)
- lowercase, kebab-case, no spaces
- scope first (`api`, `ui`, `docs`, `infra`, `data`, `tests`)

## PR size and scope

- Target **200-400 changed lines** (excluding generated files)
- Prefer **1 concern per PR** (feature, fix, refactor, docs, or test)
- If a change grows beyond ~500 lines or touches unrelated areas, split it
- Stack dependent work as separate PRs rather than one large PR

## Reviews and approvals

- Minimum **1 human review** before merge
- At least **1 reviewer who did not author the code or prompt**
- For risky areas (auth, billing, data model, deploy), require **2 reviewers**
- Author merges only after required checks pass and comments are resolved

## Agent editing rules

Agents may do without asking:

- tests, docs, comments, typing improvements
- local refactors inside files already in the PR scope
- adding files in established folders that match existing patterns

Ask first (in team chat or issue) before agent changes:

- shared interfaces/contracts used across multiple features
- database schemas/migrations, CI/CD, security/auth, dependency upgrades
- repo structure changes (new top-level folders, major moves/renames)

## Avoiding file collisions across agents

Use a lightweight **file claim** in the issue/PR thread before editing:

- `CLAIM: path/to/file.ext` (or folder)
- include expected time window (for example: `~45 min`)
- release with `UNCLAIM:` when done

If a file is already claimed, coordinate or pick a different slice.

## Commit message conventions

Use concise, reviewable commits with this format:

`type(scope): summary`

Types: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`, `ci`

Examples:

- `feat(api): add book search pagination`
- `fix(ui): handle empty suggestion state`

Rules:

- imperative voice ("add", "fix", "remove")
- first line <= 72 chars
- body (optional) explains **why** and any migration/rollout notes
- no "misc updates" or mixed-purpose commits

## Where new files go

When adding files, follow existing layout first. If no clear pattern exists, use:

- `src/features/<feature>/` feature code (UI + feature logic)
- `src/shared/` reusable components, utilities, constants
- `src/services/` API clients, external integrations
- `src/data/` schemas, adapters, persistence-related code
- `tests/` integration/e2e tests; colocated `*.test.*` for unit tests
- `docs/` design notes, decision records, runbooks
- `.github/` workflows, templates, automation config

Do not add new top-level directories unless discussed and approved.

## Definition of done for merge

- PR is scoped and titled clearly
- checks pass
- required approvals are in
- comments resolved
- docs/tests updated when behavior changed
Our goal is to keep `main` stable, reviewable, and easy for four people—and
their coding agents—to share.

## Branches and pull requests

- Never work directly on `main`. Use `firstname/short-purpose` branches, such
  as `nakyungoh/add-ingestion-tests` or `chloe/fix-login`.
- Keep a pull request focused on one user-visible change, bug fix, refactor,
  or documentation update. Prefer a reviewable change that takes about 15
  minutes to understand; split unrelated work into separate PRs.
- Open the PR against `main`, describe the behavior changed, and include
  validation steps or explain why none apply. Keep PRs draft until the change
  is ready for review.
- Every PR needs one teammate review. Changes to shared interfaces, workflows,
  or security-sensitive code need two reviewers, including an owner of the
  affected area when one exists.

## Working with coding agents

- An agent may edit files within the task's owned area, add tests and
  documentation for that change, and run the project checks without asking.
  It must not change another contributor's branch, rewrite history, commit
  secrets, or make unrelated cleanup changes.
- Before starting, claim the files or area in the PR description or team
  channel. If another agent has claimed a file, coordinate first; do not
  edit it concurrently.
- Prefer one agent per file for a task. For shared files (dependency manifests,
  lockfiles, CI configuration, routing, and top-level documentation), agree
  on an owner and integrate changes sequentially.
- If the task expands beyond its claimed area, or a design choice affects
  another contributor's work, stop and ask the team before editing.

## Commits

Use imperative, specific commit subjects:

```text
Add document ingestion endpoint
Fix empty search result handling
```

Keep commits small and buildable. Put the issue or PR reference in the body
when useful, and explain the reason for a non-obvious change. Do not combine
formatting churn with functional changes.

## Repository layout

Put new files in the directory that matches their responsibility:

```text
src/                 application code
tests/               automated tests and fixtures
docs/                user and developer documentation
scripts/             repeatable development or release scripts
.github/             workflows, templates, and repository configuration
README.md            project overview and quick start
CONTRIBUTING.md      contribution rules
```

Keep configuration at the repository root only when the tool requires it
(for example, a package manifest or formatter configuration). Create a
focused subdirectory before adding a new category of files, and update this
layout when the project grows.
