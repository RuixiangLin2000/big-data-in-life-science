# 高内涵成像（High-Content Imaging）

## 中文导读（Chinese Guide）

高内涵筛选会在多孔板中采集多个视野、通道、焦平面和时间点，并为每个细胞生成大量测量，因此单块孔板即可产生数百万条观测。

实验模型包括二维细胞、三维模型、原代细胞、患者来源模型和共培养。分析可分为针对已知表型的定向方法，以及使用广泛形态特征进行聚类、相似性搜索和机制推断的无偏分析。

流程包括实验设计、成像质控、照明校正、分割、特征提取、单细胞质控、聚合、归一化、批次校正、建模和生物学验证。自动化质控必须与有代表性的人工视觉检查结合。

---

## 英文原文（Original English）

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
