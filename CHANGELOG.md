# Changelog

All notable changes after v1.0.0 are documented here. Entries are derived from
the release tags; the linked commits and PRs hold the detail.

## [v1.2.0] - 2026-10-29

**Behaviour change (environment selection):** `apply` and
`generation pending` now fail when no environment is given, instead of
reading and writing configuration in the shared `elephant-clitools`
directory itself. Pass `--env` or set `ENV`. See [Usage](README.md#usage).

Changes:

- `configure` gains `--env`, `--alias`, `--reset-endpoints` and
  `--well-known`, which sets up `tt-stage`, `tt-prod`, `ntb-stage` and
  `ntb-prod` and makes `stage` and `prod` aliases for the TT environments.
  `configure list` shows every environment with its URLs, alias target and
  token expiry.
- An environment without an OIDC configuration gives an error naming the
  `configure` command rather than a crash, and login prompts are written to
  stderr so output can be piped while logging in.
- The `examples/tt` configuration loads again; it declared `core/organiser`
  twice.
- Dependency upgrades: clitools to v1.1.1.

## [v1.1.1] - 2026-04-22

- `eleconf diff [<dir-a>] <dir-b>` compares the `.hcl` files in two
  configuration directories, listing added, removed and changed files followed
  by unified diffs.

## [v1.1.0] - 2026-04-14

- Document blocks accept the `type#variant` notation, such as
  `core/article#timeless`, so that variants can have their own statuses and
  workflows. A variant must be declared on its base type, and variants cannot
  declare variants of their own.

## [v1.0.0] - 2026-04-13

- First stable release, managing schemas, document types, statuses,
  workflows, metrics and meta types, including schema generations.
