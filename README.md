 BWT & FM-Index Backward Search for DNA Pattern Matching

A Python implementation of the Burrows-Wheeler Transform (BWT), Inverse BWT (LF Mapping), and FM-Index Backward Search for rapid exact pattern matching in DNA sequences, supporting both forward and reverse-complement strands.

 Background
Modern short-read aligners like Bowtie and BWA rely on the Burrows Wheeler Transform and FM Index to compress large reference genomes and align millions of sequencing reads in (m) time complexity (where m is the query pattern length), independent of the reference genome size.

 Features
- BWT Construction & Suffix Array Mapping: Generates cyclic rotations, lexicographically sorts them, and extracts the BWT string alongside 0-based genomic coordinates.
- Exact Sequence Reconstruction: Implements the Last-to-First (LF) mapping property to invert the BWT back to the original DNA sequence.
- Fast Backward Search: Precomputes the C-table and cumulative occurrence cc matrix for m exact substring matching.
- Double-Stranded DNA Support: Automatically queries both the input DNA motif and its reverse complement.

Project Structure
```text
BWT-DNA-Pattern-Search/
├── bwt_dna_search.py   # Core implementation and automated demonstration
└── README.md           # Project documentation
```

 Getting Started

 Prerequisites
- Python 3.8+ (uses standard library only; no external dependencies required).

 Running the Project
Clone the repository and run the script directly:
```bash
python bwt_dna_search.py
```

Sample Output
```text
=================================================================
 BWT & FM-Index Backward Search for DNA Pattern Matching 
=================================================================

[1] Reference Sequence (Length: 120 bp):
    ATGGTGAGCAAGGGCGAGGAGCTGTTCACCGGGGTGGTGCCCATCCTGGTCGAGCTGGAC...

[2] BWT Last Column (first 60 chars):
    CGGGGGGCCCTAGGCGGCCCGCCCTGGAACGTACGTACGGGGATCCGAAAGGTTTACCCC...

[3] Inverse BWT Check: PASSED (100% identical to original sequence)

[4] Pattern Search Results (Forward & Reverse Complement):
-----------------------------------------------------------------
Query      | Strand   | Seq        | Count  | 0-Based Positions
-----------------------------------------------------------------
GGCGAG     | Forward  | GGCGAG     | 3      | [11, 97, 103]
GGCGAG     | RevComp  | CTCGCC     | 0      | []
-----------------------------------------------------------------
TTCAGC     | Forward  | TTCAGC     | 1      | [80]
TTCAGC     | RevComp  | GCTGAA     | 0      | []
-----------------------------------------------------------------
ATGCCA     | Forward  | ATGCCA     | 1      | [110]
ATGCCA     | RevComp  | TGGCAT     | 0      | []
-----------------------------------------------------------------
```
