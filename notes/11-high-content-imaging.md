# High-Content Imaging

High-content screening acquires multiple fields, channels, planes, and time points across multi-well plates. Image processing produces many measurements per cell, yielding millions of observations.

## Experimental models

Two-dimensional cultures, three-dimensional models, primary cells, patient-derived models, and co-cultures offer different tradeoffs among throughput, biological relevance, imaging difficulty, and analysis complexity.

## Strategies

Biology-directed assays measure a known phenotype. Unbiased profiling builds broad morphological representations that support clustering, similarity search, mechanism inference, and compound comparison.

## Pipeline

1. Design plates and perturbations.
2. Acquire images and instrument QC.
3. Correct illumination.
4. Segment nuclei, cells, or structures.
5. Extract features or learned embeddings.
6. Apply single-cell QC.
7. Aggregate profiles.
8. Normalize and correct batches.
9. Model and visualize.
10. Validate biologically.

Store raw images, acquisition metadata, segmentation settings, feature tables, and treatment annotations with stable identifiers.

## Failure modes

Focus variation, edge effects, segmentation errors, cell-count differences, batch effects, well/plate leakage, and missing metadata can dominate results. Automated QC should be paired with representative visual review; exhaustive manual inspection does not scale.
