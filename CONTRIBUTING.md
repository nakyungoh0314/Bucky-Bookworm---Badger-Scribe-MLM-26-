# Contributing to Badger Scribe

Keep `main` stable and reviewable for the four contributors and their coding
agents.

## Branches and pull requests

- Never work directly on `main`. Use `<name>/<short-purpose>`, for example
  `nakyungoh/add-ingestion-tests` or `chloe/fix-login`.
- Keep each PR to one coherent feature, fix, refactor, or documentation change.
  Split unrelated work. A reviewer should be able to understand the change in
  about 15 minutes.
- Target `main`, describe the behavior changed, and include checks run (or why
  none apply). Use draft status until the PR is ready.
- Every PR needs one teammate review. Shared interfaces, workflows, and
  security-sensitive changes need two reviewers, including an area owner when
  one exists.

## Working with coding agents

- An agent may edit its claimed files, add related tests or documentation, and
  run checks without asking. It must not edit another branch, rewrite history,
  commit secrets, or make unrelated cleanup changes.
- Before editing, claim the files or area in the PR description or team
  channel. If another agent has claimed a file, coordinate first; never edit
  the same file concurrently.
- Use one agent per file where possible. Assign an owner and integrate
  sequentially for shared files such as manifests, lockfiles, CI, routing, and
  top-level documentation.
- Stop and ask before expanding beyond the claim or making a design choice
  that affects another contributor's work.

## Commits

Use small, buildable commits with imperative subjects:

```text
Add document ingestion endpoint
Fix empty search result handling
```

Keep formatting-only churn separate. Put an issue or PR reference in the body
when useful, and explain non-obvious decisions.

## Repository layout

Place new files with the responsibility they serve:

```text
src/                 application code
tests/               automated tests and fixtures
docs/                user and developer documentation
scripts/             repeatable development or release scripts
.github/             workflows, templates, and repository configuration
README.md            project overview and quick start
CONTRIBUTING.md      contribution rules
```

Keep tool-required configuration at the root (for example, a package manifest
or formatter config). Create a focused directory before adding a new category
of files, and update this map when the project grows.
