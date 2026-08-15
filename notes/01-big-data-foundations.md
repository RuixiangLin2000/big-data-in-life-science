# Big Data Foundations in Life Science

## Learning objectives

- Explain why life-science datasets become “big.”
- Distinguish volume, velocity, variety, veracity, and value.
- Compare batch and streaming analysis.
- Connect data properties to infrastructure and analytical choices.

## The five Vs

- **Volume:** sequencing, microscopy, clinical imaging, and compound libraries can produce terabytes to petabytes.
- **Velocity:** instruments and automated laboratories generate data continuously or in rapid experimental cycles.
- **Variety:** tables, sequences, graphs, images, spectra, text, and metadata require different representations.
- **Veracity:** missing values, measurement error, batch effects, bias, and inconsistent metadata limit reliability.
- **Value:** storage and computation matter only if the analysis answers a useful biological or clinical question.

## Life-science examples

- Whole-genome sequencing produces raw reads much larger than the compact reference or variant representation.
- Single-cell assays combine many measured features with very large numbers of cells.
- High-content imaging produces multiple images per well, channel, time point, and field, followed by object-level features.
- Cryo-electron microscopy and clinical imaging create large image collections.
- Drug discovery combines large chemical spaces, screening data, predictions, and experimental cycles.

## Batch versus stream

**Batch analysis** stores data first and analyzes it later. It supports deep, reproducible analysis and is common in life science.

**Streaming analysis** processes observations as they arrive. It can reduce storage pressure and latency but makes quality control, state management, and reproducibility harder.

## Consequences for system design

- Move computation toward the data when transfer is expensive.
- Use parallelism only when tasks or data can be partitioned safely.
- Track metadata and provenance from acquisition onward.
- Choose file formats that support compression and the required access pattern.
- Validate that scale does not amplify poor quality, leakage, or bias.

## Common pitfalls

- Treating “more data” as automatically better data
- Ignoring transfer time and intermediate-file growth
- Separating analysis from metadata management
- Choosing distributed tools for datasets that fit comfortably on one machine
