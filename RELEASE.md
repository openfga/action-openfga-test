# Release guide

Releases use [release-please](https://github.com/googleapis/release-please), run from the GitHub UI.

## Cutting a release

1. **Actions → release-please → Run workflow**, and pick a **bump-type**:
   - `auto` (default) — infer the bump from the commits.
   - `patch` / `minor` / `major` — force it.
   - `explicit` — set an exact version in **release-version** (e.g. `0.2.0-beta.1`).
2. Review and merge the `release: v<version>` PR it opens.
3. On merge, a GPG-signed tag and a draft GitHub Release are created — publish it.

Use `explicit` after a pre-release or a manually created tag, or to step a beta; release-please can't guess the next version in those cases.

## Versioning

Pre-1.0.0: breaking changes bump the minor, everything else bumps the patch.

## Changelog

Follow [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix                   | Section       |
| ------------------------ | ------------- |
| `feat:`                  | Added         |
| `fix:`                   | Fixed         |
| `perf:`, `refactor:`     | Changed       |
| `revert:`                | Removed       |
| `docs:`                  | Documentation |
| `test:`, `ci:`, `chore:`, `release:` | hidden        |
