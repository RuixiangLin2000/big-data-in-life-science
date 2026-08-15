# Assignment 1: NGS on HPC

## Goal

Build and run a SLURM batch workflow that processes independent sequencing samples and produces variant calls relative to a reference genome.

## Conceptual workflow

1. Start with a very small test dataset.
2. locate the indexed reference and matching FASTA index.
3. Align each sample independently.
4. Sort alignments into a binary alignment format.
5. Index each sorted alignment.
6. Compute pileups against the reference.
7. Call variants.
8. Convert or inspect the final variant representation.
9. Scale the verified procedure to the larger dataset.

## HPC requirements

- Heavy processing belongs in a batch job, not on a login node.
- Use node-local temporary storage for active computation.
- Copy inputs into temporary storage and verified outputs back to persistent storage.
- Keep samples separate.
- Load and record software modules and versions.
- Estimate time, memory, and storage before scaling.
- Preserve useful standard output for review.

## File-flow model

```text
FASTQ -> alignment -> sorted BAM -> BAM index
                           |
reference FASTA + index -> pileup -> variant call -> BCF/VCF
```

## Deliverable represented in the supplied instructions

The expected submission is the scheduler output demonstrating the executed workflow. Intermediate alignment and variant files are working data rather than the primary submission.

## Review checklist

- [ ] Small test completed before full processing
- [ ] Reference build and indices match
- [ ] Every sample processed independently
- [ ] Node-local scratch used correctly
- [ ] Outputs copied back before job completion
- [ ] Tool versions visible in the log
- [ ] No credentials or personal paths in shared material
- [ ] Commands and exit status are interpretable

This page intentionally omits course-specific paths, account values, and a ready-to-submit batch script.
