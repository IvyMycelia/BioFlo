# Changelog

All notable user-visible changes to Bio-Flow are documented in this file.

Bio-Flow follows Semantic Versioning. During early development, incompatible public API changes may occur between minor versions.

## Unreleased

### Fixed

- Correct command recognition for the Bio-Flow CLI.
- Prevent missing commands and filepaths from causing invalid argument access.
- Prevent dash-only arguments from reading beyond the command string.
- Return consistent exit codes for successful and invalid invocations.

### Removed

- Remove invalid `test.flo` import.
- Remove placeholder calls `test` and `process`.

