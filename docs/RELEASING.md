# Releasing Bio-Flow

This document describes how to prepare and publish a Bio-Flow release.

Version-number rules are documented in the [Versioning Document](./VERSIONING.md).

## Release Requirements

Before beginning a release:

- planned changes must be merged into `main`
- the project must compile
- the test suite must pass
- public APIs must be documented
- the changelog must describe user-visible changes
- known limitations must be recorded

## 1. Choose the Version

Determine the next version using the [Versioning Document](./VERSIONING.md).

Examples:

- new feature: `0.2.1 —> 0.3.0`
- bug fix: `0.3.0 —> 0.3.1`
- early-development breaking change: `0.3.1 —> 0.4.0`

## 2. Create a Release Branch

Start from the latest `main`:

```bash
git switch main
git pull
git switch -c release/v0.3.0
```

Release branches should release preparation only. New features should be completed in separate pull requests before the release branch is created.

## 3. Update Release Metadata

Update the version reported by the program:

```flo
VERSION: string = "0.3.0"
```

Move the relevant entries in the [Changelog](./CHANGELOG.md) from `Unreleased` into a versioned section:

```md
## 0.3.0 - YYYY-MM-DD
```

Leave a new empty `Unreleased` section above the release.

## 4. Verify the Release

Compile the project and run all tests.

Also manually verify important user-facing commands, such as:

```text
bioflo --version
bioflo --help
```

The reported version must match the intended release.

For a release containing sequence or file-format changes, test representative valid and invalid biological inputs.

## 5. Open the Release Pull Request

Use this title:

```text
chore: prepare v0.3.0 release
```

The pull request should contain:

- the slected version
- the included features and fixes
- verification results
- known limitations

Only version metadata, changelog entries, and release-specific corrections should be added at this stage.

## 6. Merge the Release

After verification, squash merge the release pull request into `main`.

Update the local branch:

```bash
git switch main
git pull
```

## 7. Create the Tag

Create an annotated tag on the release commit:

```bash
git tag -a v0.3.0 -m "Bio-Flow v0.3.0"
git push origin v0.3.0
```

Verify that the tag points to the intended commit before publishing the release.

## 8. Publish the Release

Create a GitHub release using the tag.

Use this title format:

```text
Bio-Flow v0.3.0
```

Release notes should summarize user-visible changes:

```md
# Bio-Flow v0.3.0

This release introduces FASTA parsing.

## Added

- Single-record FASTA parsing
- Multiline sequence support
- FASTA header extraction

## Fixed

- Empty sequence handling in GC-content calculations

## Known Limitations

-- FASTQ is not supported
-- FASTA comments are not preserved
```

Do not copy the complete commit history into the release notes. Summarize what users can now do and what limitations remain.

## 9. After the Release

Confirm that:

- the Git tag is available
- the GitHub release is published
- installation or build instructions still work
- `main` reports the released version
- the [Changelog](./CHANGELOG.md) contains a new `Unreleased` section

Delete the release branch after it is merged.

## Patch Releases

Patch releases follow the same process.

For an urgent correction:

```text
fix/fasta-buffer-overflow
```

Merge the fix into `main`, then prepare a release branch such as:

```text
release/v0.3.1
```

Do not place unrelated features in a patch release.
