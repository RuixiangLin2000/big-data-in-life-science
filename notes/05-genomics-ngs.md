# 基因组学、NGS 与大数据（Genomics, NGS, and Big Data）

## 为什么基因组学属于大数据问题（Why genomics is a big-data problem）

基因组由 DNA 序列编码，但测序产生大量带噪声的片段，而不是直接得到完整基因组。规模来自测序深度、样本数、群体研究、纵向测量和多组学整合。（A genome is encoded as DNA sequence, but sequencing produces many noisy fragments rather than a finished genome. Scale arises from read depth, sample count, population studies, longitudinal measurements, and multi-omics integration.）

## 技术概念（Technology concepts）

- 短读长测序通量高且分析生态成熟。（Short-read sequencing provides high throughput and mature analysis ecosystems.）
- 长读长测序改善结构变异检测和组装，但具有不同的错误与成本特征。（Long-read sequencing improves structural variant detection and assembly but has different error and cost profiles.）
- Bulk 测序对大量细胞取平均。（Bulk sequencing averages across many cells.）
- 单细胞测序增加维度和稀疏性，同时揭示细胞异质性。（Single-cell sequencing increases dimensionality and sparsity while exposing cellular heterogeneity.）

## 常见文件类型（Common file types）

- **FASTQ：** reads 与每个碱基的质量分数（**FASTQ:** reads and per-base quality scores）
- **FASTA：** 参考序列或组装序列（**FASTA:** reference or assembled sequences）
- **SAM/BAM/CRAM：** 比对后的 reads（**SAM/BAM/CRAM:** aligned reads）
- **VCF/BCF：** 遗传变异（**VCF/BCF:** genetic variants）
- 表达分析所需的计数矩阵与元数据表（Count matrices and metadata tables for expression analyses）

## 通用 NGS 流程（Generic NGS pipeline）

1. 检查 reads 质量。（Inspect read quality.）
2. 准备并索引参考序列。（Prepare and index the reference.）
3. 比对 reads 或使用无比对方法。（Align reads or use an alignment-free method.）
4. 排序并索引比对结果。（Sort and index alignments.）
5. 定量覆盖度、表达或变异。（Quantify coverage, expression, or variants.）
6. 进行过滤和质量控制。（Apply filtering and quality control.）
7. 结合样本元数据解释结果。（Interpret results with sample metadata.）
8. 归档命令、版本、参数和校验和。（Archive commands, versions, parameters, and checksums.）

## HPC 注意事项（HPC considerations）

- 在相互独立时并行处理样本。（Process samples in parallel where independent.）
- 将参考索引保存在共享只读位置。（Keep reference indices in shared read-only locations.）
- 对高强度临时 I/O 使用本地 scratch。（Use local scratch for intensive temporary I/O.）
- 启动所有样本前估算输出增长。（Estimate output growth before launching all samples.）
- 避免不必要地复制完整数据集。（Avoid copying entire datasets unnecessarily.）

## 解释层面的挑战（Interpretation challenges）

主要挑战包括测序与比对错误、参考偏差、批次效应、群体结构、多重检验、功能注释不足，以及基因组数据本身具有可识别性所带来的隐私风险。（Challenges include sequencing and mapping errors; reference bias; batch effects and population structure; multiple testing; incomplete functional annotation; and privacy risks because genomic data are identifying.）

基因组分析必须把计算扩展能力与谨慎的生物学解释和治理结合起来。（Genomic analysis must combine computational scalability with careful biological interpretation and governance.）
