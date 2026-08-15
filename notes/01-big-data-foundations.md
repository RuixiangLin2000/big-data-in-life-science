# 生命科学中的大数据基础（Big Data Foundations in Life Science）

## 学习目标（Learning objectives）

- 解释生命科学数据为何会成为“大数据”。（Explain why life-science datasets become “big.”）
- 区分体量、速度、多样性、真实性和价值。（Distinguish volume, velocity, variety, veracity, and value.）
- 比较批处理与流处理分析。（Compare batch and streaming analysis.）
- 将数据特性与基础设施和分析方法的选择联系起来。（Connect data properties to infrastructure and analytical choices.）

## 五个 V（The five Vs）

- **体量（Volume）：** 测序、显微成像、临床影像和化合物库可能产生 TB 到 PB 级数据。（**Volume:** sequencing, microscopy, clinical imaging, and compound libraries can produce terabytes to petabytes.）
- **速度（Velocity）：** 仪器和自动化实验室会持续或以快速实验周期产生数据。（**Velocity:** instruments and automated laboratories generate data continuously or in rapid experimental cycles.）
- **多样性（Variety）：** 表格、序列、图、图像、光谱、文本和元数据需要不同的表示方式。（**Variety:** tables, sequences, graphs, images, spectra, text, and metadata require different representations.）
- **真实性（Veracity）：** 缺失值、测量误差、批次效应、偏差和不一致的元数据会限制可靠性。（**Veracity:** missing values, measurement error, batch effects, bias, and inconsistent metadata limit reliability.）
- **价值（Value）：** 只有当分析能够回答有意义的生物或临床问题时，存储与计算才有价值。（**Value:** storage and computation matter only if the analysis answers a useful biological or clinical question.）

## 生命科学实例（Life-science examples）

- 全基因组测序产生的原始 reads 远大于紧凑的参考序列或变异表示。（Whole-genome sequencing produces raw reads much larger than the compact reference or variant representation.）
- 单细胞分析把大量测量特征与极多细胞结合起来。（Single-cell assays combine many measured features with very large numbers of cells.）
- 高内涵成像会针对每个孔、通道、时间点和视野生成多幅图像，随后还会产生对象级特征。（High-content imaging produces multiple images per well, channel, time point, and field, followed by object-level features.）
- 冷冻电镜和临床成像会形成大型图像集合。（Cryo-electron microscopy and clinical imaging create large image collections.）
- 药物发现结合了庞大的化学空间、筛选数据、预测和实验循环。（Drug discovery combines large chemical spaces, screening data, predictions, and experimental cycles.）

## 批处理与流处理（Batch versus stream）

**批处理分析**先保存数据，之后再进行分析。它支持深入、可复现的分析，在生命科学中很常见。（**Batch analysis** stores data first and analyzes it later. It supports deep, reproducible analysis and is common in life science.）

**流处理分析**在观测到达时立即处理。它可以降低存储压力和延迟，但会增加质量控制、状态管理和可复现性的难度。（**Streaming analysis** processes observations as they arrive. It can reduce storage pressure and latency but makes quality control, state management, and reproducibility harder.）

## 对系统设计的影响（Consequences for system design）

- 当数据传输成本高时，应让计算靠近数据。（Move computation toward the data when transfer is expensive.）
- 只有在任务或数据可以安全拆分时才使用并行计算。（Use parallelism only when tasks or data can be partitioned safely.）
- 从数据采集开始就追踪元数据和数据来源。（Track metadata and provenance from acquisition onward.）
- 根据压缩需求和访问模式选择文件格式。（Choose file formats that support compression and the required access pattern.）
- 验证规模扩大是否放大了低质量、数据泄漏或偏差。（Validate that scale does not amplify poor quality, leakage, or bias.）

## 常见误区（Common pitfalls）

- 把“更多数据”当作自动等于“更好的数据”（Treating “more data” as automatically better data）
- 忽视传输时间和中间文件增长（Ignoring transfer time and intermediate-file growth）
- 将分析与元数据管理分离（Separating analysis from metadata management）
- 对能够轻松装入单机的数据集使用分布式工具（Choosing distributed tools for datasets that fit comfortably on one machine）
