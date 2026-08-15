# 生命科学中的大数据基础（Big Data Foundations in Life Science）

## 中文导读（Chinese Guide）

本章介绍大数据的五个核心维度：体量、速度、多样性、真实性和价值。测序、单细胞实验、显微成像、临床影像和药物发现都会产生规模巨大且类型复杂的数据。

批处理适合先保存数据、再进行深入和可复现的分析；流处理适合实时数据，但对质量控制、状态管理和复现提出更高要求。系统设计时应尽量让计算靠近数据，完整记录元数据与来源，并根据访问模式选择文件格式。

常见误区包括把“更多数据”等同于“更好数据”、忽视传输和中间文件成本、丢失元数据，以及对小数据集过度使用分布式工具。

---

## 英文原文（Original English）

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
