# Changelog

All notable user-visible changes to Bio-Flow are documented in this file.

Bio-Flow follows Semantic Versioning. During early development, incompatible public API changes may occur between minor versions.

## Unreleased

## 0.1.0 - 2026-07-20

### Added

- Initial Bio-Flow command-line interface.
- Help and version commands.
- DNA sequence validation with support for the unknown `N` bases.
- Nucleotide and GC-base counting.
- GC-content calculation.

### Fixed

- Correct command recognition for the Bio-Flow CLI.
- Prevent missing commands and filepaths from causing invalid argument access.
- Prevent dash-only arguments from reading beyond the command string.
- Return consistent exit codes for successful and invalid invocations.
