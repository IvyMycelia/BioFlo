# Bio-Flow

A bioinformatics library written in Flower.

Bio-Flow aims to provide tools for processing biological sequences and FASTA files. It is currently under development.

## Current Features

- DNA sequence validation
- Nucleotide counting
- GC-base counting
- GC-content calculation

See [`docs/sequence.md`](docs/usage/sequence.md) for the sequence API.

## Build

```bash
./Flower main.flo bin/bioflo
```

## Test

```bash
./Flower tests/sequence.flo /tmp/bioflow-sequence-tests
./tmp/bioflow-sequence-tests
```
