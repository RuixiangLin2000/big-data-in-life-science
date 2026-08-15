# 基因组学、NGS 与大数据（Genomics, NGS, and Big Data）

## 中文导读（Chinese Guide）

测序产生的是大量带噪声的片段，而不是直接得到完整基因组。数据规模来自测序深度、样本数量、群体研究、单细胞实验和多组学整合。

常用格式包括 FASTQ、FASTA、SAM/BAM/CRAM 和 VCF/BCF。典型流程包含质量检查、参考序列准备、比对、排序与索引、定量或变异检测、过滤、解释和来源记录。

在集群上应按独立样本并行处理，在节点本地存储中完成密集临时 I/O，并提前估算中间文件规模。结果解释还需考虑测序错误、参考偏差、批次效应、群体结构、多重检验、注释不足和基因组隐私。

---

## 英文原文（Original English）

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
