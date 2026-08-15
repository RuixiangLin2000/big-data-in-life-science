# Genomics, NGS, and Big Data

## Why genomics is a big-data problem

A genome is encoded as DNA sequence, but sequencing produces many noisy fragments rather than a finished genome. Scale arises from read depth, sample count, population studies, longitudinal measurements, and multi-omics integration.

## Technology concepts

- Short-read sequencing provides high throughput and mature analysis ecosystems.
- Long-read sequencing improves structural variant detection and assembly but has different error and cost profiles.
- Bulk sequencing averages across many cells.
- Single-cell sequencing increases dimensionality and sparsity while exposing cellular heterogeneity.

## Common file types

- **FASTQ:** reads and per-base quality scores
- **FASTA:** reference or assembled sequences
- **SAM/BAM/CRAM:** aligned reads
- **VCF/BCF:** genetic variants
- Count matrices and metadata tables for expression analyses

## Generic NGS pipeline

1. Inspect read quality.
2. Prepare and index the reference.
3. Align reads or use an alignment-free method.
4. Sort and index alignments.
5. quantify coverage, expression, or variants.
6. Apply filtering and quality control.
7. Interpret results with sample metadata.
8. Archive commands, versions, parameters, and checksums.

## HPC considerations

- Process samples in parallel where independent.
- Keep reference indices in shared read-only locations.
- Use local scratch for intensive temporary I/O.
- Estimate output growth before launching all samples.
- Avoid copying entire datasets unnecessarily.

## Interpretation challenges

- Sequencing and mapping errors
- Reference bias
- Batch effects and population structure
- Multiple testing
- Incomplete functional annotation
- Privacy risks because genomic data are identifying

Genomic analysis must combine computational scalability with careful biological interpretation and governance.
