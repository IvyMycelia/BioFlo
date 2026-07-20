# DNA Sequence Analysis

Bio-Flow provides basic functions for validating and analyzing DNA sequences.

Import the sequence module:

```flo
import "bio/sequence.flo" as sequence
```

## Validation

```flo
valid: bool = sequence.is_valid_dna_sequence("ACGTN")
```

Valid DNA sequences may contain:

```text
A C G T N
```

`N` represents an unknown nucleotide.

Validation is currently case-sensitive. Empty and lowercase sequences are not considered valid.

## Nucleotide Counting

```flo
count: int = sequence.count_nucleotide("AACGT", 'A')
```

`count_nucleotide` counts exact matches for the requested character.

## GC Count

```flo
count: int = sequence.gc_count("ACGT")
```

`gc_count` returns the number of `G` and `C` bases.

## GC Content

```flo
content: double = sequence.gc_content("ACGT")
```

`gc_content` returns a fraction between `0.0` and `1.0`.

An empty sequence returns `0.0`.
