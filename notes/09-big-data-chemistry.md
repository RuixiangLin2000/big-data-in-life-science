# 大数据驱动的化学与药物发现（Big Data-Driven Chemistry and Drug Discovery）

药物发现是高失败率的多阶段优化过程。计算方法支持靶点选择、分子设计、合成规划、实验分析、安全性预测和临床转化。（Drug discovery is a multi-stage optimization process with high attrition. Computational methods support target selection, compound design, synthesis planning, assay analysis, safety prediction, and clinical translation.）

## 设计—合成—测试—分析（Design-Make-Test-Analyze）

该循环提出分子、合成分子、测量性质并更新证据；计算工具可在设计与合成之间对实验进行优先排序。（The cycle proposes molecules, synthesizes them, measures properties, and updates the evidence. Computational tools prioritize experiments between design and synthesis.）

## 数据与建模（Data and modeling）

数据来源包括化学结构、反应、实验测定、ADME、药代动力学、毒理学、组学、成像、文献、模拟和先前预测。（Data sources include chemical structures, reactions, assays, ADME, pharmacokinetics, toxicology, omics, imaging, literature, simulations, and previous predictions.）

模型可预测活性、选择性、性质、安全性、合成和反应结果。分子可表示为描述符、指纹、图、字符串、构象或学习得到的嵌入。（Models support activity, selectivity, property, safety, synthesis, and reaction predictions. Molecules can be represented by descriptors, fingerprints, graphs, strings, conformations, or learned embeddings.）

## 生成式设计（Generative design）

生成模型可以提出候选物，但必须受到可合成性、新颖性、安全性、不确定性和多目标约束，实验确认仍不可缺少。（Generative models propose candidates but must be constrained by synthesizability, novelty, safety, uncertainty, and multiple objectives. Experimental confirmation remains essential.）

## 基础设施与风险（Infrastructure and risks）

有用的基础设施包括标准化化学登记、可扩展相似性搜索、共享特征计算、实验追踪、主动学习，以及把预测连接到实验结果的数据来源记录。（Useful infrastructure includes standardized chemical registration, scalable similarity search, shared feature computation, experiment tracking, active learning, and provenance linking predictions to laboratory outcomes.）

需要警惕重复化合物、实验泄漏、时间泄漏、历史决策偏差、定义不清的适用域，以及优化代理指标而非实验价值。（Watch for duplicated compounds, assay leakage, temporal leakage, biased historical decisions, poorly defined applicability domains, and optimization of proxy metrics rather than experimental value.）
