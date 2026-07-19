# Versioning

Bio-Flow follows [Semantic Versioning](https://semver.org/) using the format:

```text
MAJOR.MINOR.PATCH
```

For example:

```text
0.3.1
```

## Version Numbers

A version consists of:

- `MAJOR`: incompatible changes to the stable public API
- `MINOR`: new backward-compatible functionality
- `PATCH`: backward-compatible bug fixes

Bio-Flow is currently in early development, so released use a major version of `0`.

During this period:

- new features increment `MINOR`
- breaking API changes also increment `MINOR`
- backward-compatible fixes increment `PATCH`

Examples:

```text
0.1.0 –> 0.2.0  New feature or early-development API change
0.2.0 –> 0.2.1  Backward-compatible bug fix
0.2.1 –> 0.3.0  Another new feature
```

Version `1.0.0` will indicate that Bio-Flo public API is considered stable.

After `1.0.0`, incompatible public API changes will increment `MAJOR`.

## Git Tags

Release tags include a `v` prefix:

```text
v0.1.0
v0.2.0
v1.0.0
```

The version stored in the source omits the prefix:

```flo
VERSION: string = "0.1.0"
```

The `v` identifies a Git release tag explicitly; it is not part of the direct version number of the program.

## Pre-releases

Unstable releases may use these suffixes:

```text
v0.3.0-alpha.1
v0.3.0-beta.1
v0.3.0-rc.1
```

Their meanings are:

- `alpha`: incomplete and expected to change
- `beta`: feature-complete but still being tested
- `rc`: a release candidate awaiting final verification

Small releases may skip pre-release versions entirely.

## Deciding the Next Version

Use the following rules:

1. If functionality was added, increment `MINOR`.
2. If existing functionality was fixed, increment `PATCH`.
3. If an early-development API was changed incompatibly, increment `MINOR`.
4. Aftr `1.0.0`, increment `MAJOR` for incompatible API changes.

Examples:

| Change                         | Current | Next
|   ---                          |   ---:  | ---: |
| Fix GC-content calculation     | `0.2.0` | `0.2.1`
| Add FASTA parsing              | `0.2.1` | `0.3.0`
| Rename an API before `1.0`     | `0.3.0` | `0.4.0`
| Break a stable API after `1.0` | `1.4.2` | `2.0.0`

## Public API

The public API consists of declarations exported with `prop`.

Changes to private functions and internal implementation details do not require a breaking version unless they change public behavior.

Public API changes include:

- adding, removing, or renaming exported functions
- changing exported function parameters
- changing exported return types
- changing exported struct or their accessible fields
- changing documented ownership requirements
- changing documented error behavior
