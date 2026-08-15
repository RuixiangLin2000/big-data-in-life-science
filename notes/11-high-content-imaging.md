# 高内涵成像（High-Content Imaging）

高内涵筛选会在多孔板上采集多个视野、通道、平面和时间点，每个细胞还会产生大量测量，从而形成数百万条观测。（High-content screening acquires multiple fields, channels, planes, and time points across multi-well plates. Image processing produces many measurements per cell, yielding millions of observations.）

## 实验模型（Experimental models）

二维培养、三维模型、原代细胞、患者来源模型和共培养在通量、生物相关性、成像难度和分析复杂度之间具有不同权衡。（Two-dimensional cultures, three-dimensional models, primary cells, patient-derived models, and co-cultures offer different tradeoffs among throughput, biological relevance, imaging difficulty, and analysis complexity.）

## 分析策略（Strategies）

生物学定向实验测量已知表型；无偏分析建立广泛的形态表示，用于聚类、相似性搜索、机制推断和化合物比较。（Biology-directed assays measure a known phenotype. Unbiased profiling builds broad morphological representations that support clustering, similarity search, mechanism inference, and compound comparison.）

## 流程（Pipeline）

1. 设计孔板和扰动。（Design plates and perturbations.）
2. 采集图像并进行仪器质控。（Acquire images and instrument QC.）
3. 校正照明。（Correct illumination.）
4. 分割细胞核、细胞或其他结构。（Segment nuclei, cells, or structures.）
5. 提取特征或学习得到的嵌入。（Extract features or learned embeddings.）
6. 进行单细胞质控。（Apply single-cell QC.）
7. 聚合表型。（Aggregate profiles.）
8. 归一化并校正批次。（Normalize and correct batches.）
9. 建模并可视化。（Model and visualize.）
10. 进行生物学验证。（Validate biologically.）

应使用稳定标识保存原始图像、采集元数据、分割设置、特征表和处理注释。（Store raw images, acquisition metadata, segmentation settings, feature tables, and treatment annotations with stable identifiers.）

## 失败模式（Failure modes）

焦点变化、边缘效应、分割错误、细胞数量差异、批次效应、孔板泄漏和元数据缺失都可能主导结果。自动化质控应配合有代表性的视觉复核，穷举式人工检查无法扩展。（Focus variation, edge effects, segmentation errors, cell-count differences, batch effects, well/plate leakage, and missing metadata can dominate results. Automated QC should be paired with representative visual review; exhaustive manual inspection does not scale.）
