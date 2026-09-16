# Contributing to Badger Scribe

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
