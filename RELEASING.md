# Releasing

Releases are automated with [release-please](https://github.com/googleapis/release-please).

## Cutting a release

1. Go to **Actions → release-please → Run workflow**. Pick a bump type: `auto` follows conventional commits, `patch`/`minor`/`major` force that bump, and `explicit` uses the exact version entered in `release-version`.
2. release-please opens a PR titled `release: vX.Y.Z` that bumps the version in `.release-please-manifest.json` and the `README.md` usage examples, and updates `CHANGELOG.md`. Review it.
3. Merge it. CI pushes a signed `vX.Y.Z` tag and a draft GitHub release, then undrafts it.

## Version bumps

Bumps follow [conventional commits](https://www.conventionalcommits.org/), with `bump-minor-pre-major` and `bump-patch-for-minor-pre-major` enabled:

| Commit | Before v1.0.0 | v1.0.0 and later |
|---|---|---|
| `feat:` | patch | minor |
| `fix:`, `perf:`, `refactor:`, `revert:`, `docs:` | patch | patch |
| `type!:` or `BREAKING CHANGE:` footer | minor | major |

## Changelog

Built from commit messages since the last release: `feat:` → Added, `fix:` → Fixed, `perf:`/`refactor:` → Changed, `revert:` → Removed, `docs:` → Documentation. `test:`, `ci:` and `chore:` commits are hidden.

### Overriding an entry

If a commit message isn't user-facing, add this block to the PR description. This also works after merging: edit the merged PR's description, then re-run the release workflow. release-please uses it instead of the commit message:

```
BEGIN_COMMIT_OVERRIDE
feat: user-facing description of the change
END_COMMIT_OVERRIDE
```

### Breaking changes

Mark the type with `!` and add a `BREAKING CHANGE:` footer in the squash commit when merging. GitHub prefills the title from the commit for single-commit PRs and from the PR title otherwise, so confirm the `!` is there and add the footer to the body:

```
feat!: remove the Foo option

BREAKING CHANGE: the Foo option has been removed. Use Bar instead.
```

This gets its own changelog section and triggers a major bump (minor before v1.0.0).
