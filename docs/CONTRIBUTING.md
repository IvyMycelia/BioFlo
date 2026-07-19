# Contirbuting to Bio-Flow

Bio-Flow is a bioinformatics library written in Flower. Contributions should be focused, tested, and consistent with Flower's explicit memory and module model.

## Development Workflow

Create a branch from the latest `main`:

```bash
git switch main
git pull
git switch -c feature/dna-validation
```

Make on focused change, compile it, test it, and open a pull request.

After the pull request is merged, delete the branch.

## Branch Names

Use one of these prefixes:

- `feature/` for new functionality
- `fix/` for bug fixes
- `docs/` for documentation
- `test/` for test-only changes
- `refactor/` for internal restructuring
- `perf/` for performance improvements
- `build/` for build-system changes
- `chore/` for repository maintenance
- `release/` for release preparation
- `experiment/` for uncertain or disposable experiments

Examples:

```text
feature/fasta-parser
fix/cli-missing-path
docs/versioning
test/gc-content
refactor/sequence-validation
release/v0.2.0
```

Branches should be short-lived and limited to one specific coherent purpose.

## Commit Messages

Bio-Flow uses Conventional Commit messages:

```text
type(scope): short description
```

Examples:

```text
feat(sequence): add DNA validation
fix(fasta): handle empty records
docs(readme): describe project goals
test(sequence): cover ambigious bases
refactor(cli): separate command dispatch
chore: prepare v0.2.0 release
```

## Commit Types

- `feat`: user-visible functionality
- `fix`: faulty behavior corrected
- `docs`: documentation only
- `test`: tests only
- `refactor`: restructuring without a behavioral change
- `perf`: performance improvement
- `build`: compiler, build, or packaging changes
- `ci`: continuous-integration changes
- `chore`: maintenance not covered by another type

## Scopes

Common scopes include:

```text
seauence
fasta
fastq
transcription
translation
io
cli
docs
tests
```

Scopes are optional when a change affects the whole project.

## Writing the Description

The description should:

- use the imperative form. such as `add`, `fix`, or `remove`
- begin with a lowercase letter
- describe one coherent change
- omit the final period
- remain concise

Good:

```text
feat(sequence): calculate GC content
```

Avoid:

```text
updated stuff
```

For larger changes, add a body explaining the motivation or important design decisions:

```text
feat(fasta): parse multiline sequence records

Accuulate sequence lines until the next header instead of treating lines as a separate record.

Reject sequence data that appears before the first FASTA header.
```

## Breaking Changes

Mark an incompatible public API change with `!`:

```text
feat(sequence)!: return validation results instead of bool
```

Explain the incompatibility in the commit body:

```text
BREAKING CHANGE: is_valid_dna now returns ValidationResult instead of bool
```

## Commit Scope

A commit should represent one complete idea.

A good commit should:

- compile whenever possible
- contain related changes
- be understandable during review
- be safe to revert independently

Do not combine unrelated features, fixes, and documentation cleanup in one commit.

Tests may be committed with the implementation they verify. They do not need a separate commit unless the test change is independently meaningful.

## Pull Requests

Every feature and fix should be submitted through a pull request.

A pull request should:

- have a Conventional Commit-style title
- explain the result of the change
- describe how it was tested
- identify limitations or unresolved questions
- remain focused on one outcome

Example title:

```text
feat(sequence): add DNA validation
```

Draft pull requests may be used for incomplete work or early design feedback.

## Merging

Squash merging is the default.

Development commits such as experiments, typo corrections, and intermediate fixes should become on clear commit on `main`.

The pull request title normally becomes the squash commit message.

Rebase merging may be used when every commit is intentionally structured and worth preserving.

Do not merge a pull request until:

- the code compiles
- relevant tests pass
- the public API is documented
- ownership and cleanup requirements are clear
- review comments are resolved

## Code Style

Use:

- four spaces for indentation
- descriptive names
- one statement per line when practical
- `prop` only for intentional public APIs
- private helper functions by default
- explicit ownership and cleanup behavior

Functions that allocate memory should clearly document who owns the returned memory and how it must be released.

## Reporting Problems

A useful bug report should include:

- the Bio-Flow version
- the Flower compiler version
- the operating system
- a minimal input that reproduces the problem
- expected behavior
- actual behavior
- compiler or runtime output
