# 2026 年 6 月考试回忆题（June 2026 Recalled Exam Questions）

> 本页根据考后回忆和手写记录整理，并非官方试卷；题目措辞、选项与分值可能和原卷不同。（This page is reconstructed from post-exam memory and handwritten notes. It is not an official exam paper; wording, options, and marks may differ from the original.）
>
> 置信度分为高、中、低，仅表示对题目轮廓的记忆程度。（Confidence is marked high, medium, or low and refers only to how clearly the question outline was remembered.）

## 较明确的回忆题（Relatively clear recalled questions）

### 1. 生命科学大数据与 3V（Big data in life science and the 3Vs）

**置信度：高（Confidence: high）**

解释大数据对生命科学的意义，并结合体量、多样性和速度三个 V，每项给出两个例子。（Explain the significance of big data in life science using the three Vs—volume, variety, and velocity—and give two examples for each.）

答题线索（Answer outline）：

- 体量：全基因组测序数据；高内涵成像产生的大规模图像。（Volume: whole-genome sequencing data; large image collections from high-content imaging.）
- 多样性：基因组、转录组和蛋白质组等多组学数据；图像、临床表格和自由文本等不同数据形式。（Variety: multi-omics data such as genomics, transcriptomics, and proteomics; different formats such as images, clinical tables, and free text.）
- 速度：测序仪持续产生数据；实时传感器或患者监测数据流。（Velocity: continuous output from sequencing instruments; real-time streams from sensors or patient monitoring.）
- 意义：这些数据可以支持机制发现、患者分层和预测，但也带来存储、计算、质量控制、隐私与复现方面的挑战。（Significance: these data can support mechanistic discovery, patient stratification, and prediction, while creating challenges in storage, computation, quality control, privacy, and reproducibility.）

### 2. AI 共同研究者论文：整合与合成（AI co-investigator paper: aggregation and synthesis）

**置信度：中高（Confidence: medium-high）**

结合 Seminar 论文，说明大语言模型参与科研的两种形式——信息整合与知识合成——以及它们如何实现。（Using the seminar paper, explain two ways in which large language models participate in research—information aggregation and knowledge synthesis—and how they are performed.）

答题线索（Answer outline）：

- 信息整合把已有文献、数据库结果或多位智能体的输出收集、筛选并组织起来。（Information aggregation collects, filters, and organizes existing literature, database results, or outputs from multiple agents.）
- 知识合成在整合材料的基础上建立联系、提出解释或假设，并形成可检验的研究方向。（Knowledge synthesis connects the aggregated material, proposes explanations or hypotheses, and develops testable research directions.）
- 可能的实现包括检索增强生成、工具调用、多智能体分工、候选答案比较、批评与修订，以及增加推理时计算。（Possible mechanisms include retrieval-augmented generation, tool use, multi-agent division of labor, candidate comparison, critique and revision, and increased inference-time compute.）
- 两者都需要来源核查、人工判断与实验验证；流畅文本不等于科学证据。（Both require source verification, human judgment, and experimental validation; fluent text is not equivalent to scientific evidence.）

### 3. 自监督、监督与无监督学习（Self-supervised, supervised, and unsupervised learning）

**置信度：高（Confidence: high）**

解释自监督学习的基本原则，并比较监督学习和无监督学习。（Explain the principle of self-supervised learning and compare supervised with unsupervised learning.）

答题线索（Answer outline）：

- 监督学习使用人工或实验提供的标签，学习输入到目标的映射。（Supervised learning uses human- or experiment-provided labels to learn a mapping from inputs to targets.）
- 无监督学习不依赖目标标签，寻找聚类、低维表示或数据分布等结构。（Unsupervised learning does not rely on target labels and seeks structures such as clusters, low-dimensional representations, or the data distribution.）
- 自监督学习也不需要人工标签，但会从数据本身构造代理标签，例如遮盖部分序列后预测缺失内容，或比较同一样本的不同增强视图。（Self-supervised learning also avoids manual labels but constructs proxy targets from the data itself, for example by masking part of a sequence and predicting it, or by comparing augmented views of the same sample.）
- 预训练得到的表示通常再用于带少量标签的下游任务。（The pretrained representation is commonly reused for downstream tasks with limited labeled data.）

### 4. 为什么验证曲线比训练曲线波动更大（Why validation curves fluctuate more than training curves）

**置信度：高（Confidence: high）**

给出训练集和验证集的损失或准确率曲线，解释为什么验证曲线的波动通常更明显。（Given training and validation loss or accuracy curves, explain why the validation curve often fluctuates more.）

答题线索（Answer outline）：

- 验证集通常更小，因此指标估计的方差更大，少数困难样本便可能明显改变结果。（The validation set is usually smaller, so its metric estimate has higher variance and a few difficult samples can change the result noticeably.）
- 训练指标常由许多 mini-batch 平均得到，而且模型直接优化训练损失，因此曲线更平滑。（Training metrics are often averaged over many mini-batches, and the model directly optimizes training loss, so the curve is smoother.）
- 随机采样、数据增强、类别不平衡和验证样本代表性不足也会增加波动。（Random sampling, augmentation, class imbalance, and an unrepresentative validation set can also increase fluctuations.）
- 验证损失持续升高而训练损失继续下降时，应考虑过拟合；单次小幅波动本身不等于过拟合。（If validation loss keeps rising while training loss keeps falling, overfitting should be considered; a small isolated fluctuation is not by itself proof of overfitting.）

### 5. 代码中的欠拟合与 Dropout（Underfitting and Dropout in code）

**置信度：中（Confidence: medium）**

题目可能给出一段机器学习或深度学习代码和欠拟合现象，要求指出应删除或修改哪一行；回忆中的关键词可能是被误记为 “drought” 的 `Dropout`。（The question may have shown machine-learning or deep-learning code with underfitting and asked which line should be removed or changed; the remembered word “drought” was likely `Dropout`.）

答题线索（Answer outline）：

- 如果训练集和验证集表现都差、两者差距又小，模型可能欠拟合。（If both training and validation performance are poor with a small gap, the model may be underfitting.）
- 过强的 Dropout 会降低有效模型容量；可以删除该层或降低 dropout rate。（Excessive Dropout reduces effective model capacity; the layer can be removed or its dropout rate reduced.）
- 该判断必须结合曲线和其余代码；若训练表现很好而验证表现差，删除 Dropout 反而可能加重过拟合。（This conclusion must be checked against the curves and the rest of the code; if training performance is strong but validation performance is poor, removing Dropout may worsen overfitting.）

### 6. Docker、虚拟机与云计算判断题（Docker, virtual machines, and cloud computing statements）

**置信度：中高（Confidence: medium-high）**

可能出现以下判断或选择内容（The following statements may have appeared as true/false or multiple-choice items）：

- “每个 Docker 容器都运行完整的独立访客操作系统”通常错误；容器通常共享宿主机内核。（“Each Docker container runs a complete independent guest operating system” is generally false; containers normally share the host kernel.）
- “云虚拟机永远不给用户 root 或管理员权限”错误；权限取决于服务和配置。（“A cloud VM never gives the user root or administrator privileges” is false; access depends on the service and configuration.）
- 虚拟化可以让一台物理机运行多个隔离的虚拟机。（Virtualization allows one physical machine to run multiple isolated virtual machines.）
- 容器通常比完整虚拟机轻量、启动更快，但它们并不是在所有安全属性上都等同于虚拟机。（Containers are usually lighter and start faster than full virtual machines, but they are not equivalent to VMs in every security property.）
- 云计算是否减少研究组的系统管理负担取决于服务模型；托管服务往往减少本地维护，但不会消除配置、安全与成本管理。（Whether cloud computing reduces a research group’s system-administration burden depends on the service model; managed services often reduce local maintenance but do not eliminate configuration, security, and cost management.）

### 7. Spark 惰性求值、动作与缓存（Spark lazy evaluation, actions, and caching）

**置信度：高（Confidence: high）**

代码轮廓可能类似于先用 `map` 生成指纹 RDD，再调用 `count()` 和 `first()`，要求判断执行和物化行为。（The code outline may have created a fingerprint RDD with `map`, followed by `count()` and `first()`, and asked about execution and materialization.）

答题线索（Answer outline）：

- `map` 是惰性 transformation，不会立即计算所有结果。（`map` is a lazy transformation and does not immediately compute all results.）
- `count()` 与 `first()` 都是 action，会触发执行。（Both `count()` and `first()` are actions and trigger execution.）
- `count()` 不会自动缓存 RDD。（`count()` does not automatically cache the RDD.）
- 如果未调用 `cache()` 或 `persist()`，后续 `first()` 会重新计算得到首条记录所需的 lineage，但通常不需要物化整个 RDD。（Without `cache()` or `persist()`, a later `first()` recomputes the lineage needed to obtain the first record, but usually does not materialize the entire RDD.）

### 8. Spark 工作节点失败后的恢复（Spark recovery after a worker failure）

**置信度：高（Confidence: high）**

在大规模分子指纹计算中，如果某个工作节点失败，Spark 会怎么处理？（During large-scale molecular fingerprint computation, what happens if a worker node fails?）

答题线索（Answer outline）：

Spark 根据 RDD lineage 在可用节点上重新计算丢失的分区，而不是从头重新运行整个数据集；前提是输入数据和计算依赖仍然可访问。（Spark uses the RDD lineage to recompute lost partitions on available nodes rather than rerunning the entire dataset, provided that the input data and dependencies remain accessible.）

### 9. 为什么高内涵成像属于大数据（Why high-content imaging is big data）

**置信度：中高（Confidence: medium-high）**

可能要求选择正确理由（The question may have asked for the correct reasons）：

- 图像数量多、体积可达 TB 级，需要可扩展或分布式存储与计算。（The image collection can reach terabyte scale and require scalable or distributed storage and computation.）
- 每个细胞可以提取数百至数千个数值特征，形成高维数据。（Hundreds or thousands of numerical features may be extracted per cell, creating high-dimensional data.）
- “仅仅因为生物学问题复杂”不足以构成大数据理由。（“Because the biological question is complex” alone is not a sufficient big-data reason.）
- 数据通常不能只靠一个小型电子表格完整管理。（The data usually cannot be fully managed with a small spreadsheet.）
- 挑战不仅是存储，还包括图像分割、特征提取、批次效应、统计分析和模型验证。（The challenge is not storage alone; it also includes segmentation, feature extraction, batch effects, statistical analysis, and model validation.）

## 不完整的题目轮廓（Incomplete question outlines）

### 10. QSAR 或虚拟筛选情景题（QSAR or virtual-screening scenario）

**置信度：低（Confidence: low）**

回忆中包含一个较小的已标注化合物集合、活性与非活性类别不平衡、建立模型后筛选约百万级化合物，并选择排名靠前的一小部分。（The recollection includes a relatively small labeled compound set, an imbalance between active and inactive classes, model building followed by screening roughly a million compounds, and selection of a small top-ranked fraction.）

可能考点（Possible concepts）：

- 类别不平衡与合适的评价指标，例如 precision-recall、balanced accuracy 或 MCC，而不只看 accuracy。（Class imbalance and suitable metrics such as precision-recall, balanced accuracy, or MCC rather than accuracy alone.）
- 数据泄漏与 scaffold split；随机切分可能让相似化合物同时出现在训练集和测试集。（Data leakage and scaffold splitting; random splitting may place similar compounds in both training and test sets.）
- 适用域、不确定性与外推风险。（Applicability domain, uncertainty, and extrapolation risk.）
- 小样本下的过拟合、交叉验证与独立实验验证。（Overfitting with small datasets, cross-validation, and independent experimental validation.）

具体数字和原始问法无法可靠恢复，因此不应把本节当作原题。（The exact numbers and original wording cannot be recovered reliably, so this section should not be treated as the original question.）

### 11. MobileNetV2 代码诊断（MobileNetV2 code diagnosis）

**置信度：低（Confidence: low）**

回忆中可能给出冻结 MobileNetV2 主干并连接分类层的代码，要求指出前两处问题。（The recalled question may have shown code that freezes a MobileNetV2 backbone and attaches a classifier, asking for the first two problems.）

可能考点（Possible concepts）：

- 若设置 `weights=None` 后又设置 `base_model.trainable = False`，被冻结的是随机初始化特征；迁移学习通常应加载预训练权重，或允许随机初始化的主干参与训练。（If `weights=None` is followed by `base_model.trainable = False`, randomly initialized features are frozen; transfer learning normally loads pretrained weights or allows a randomly initialized backbone to train.）
- 若 `pooling=None`，主干输出仍是空间特征图；连接 Dense 层前通常需要 `GlobalAveragePooling2D`、其他 pooling，或在明确理解参数代价时使用 Flatten。（With `pooling=None`, the backbone still outputs a spatial feature map; a `GlobalAveragePooling2D` or another pooling step is normally needed before Dense layers, or Flatten may be used with awareness of its parameter cost.）

## 使用方式（How to use this page）

以概念和推理链为复习重点，不要死记本页重建的措辞。（Study the concepts and reasoning chains rather than memorizing the reconstructed wording on this page.）

如以后回忆起新的细节，应继续标注置信度，并把“确定内容”和“推测内容”分开。（If new details are remembered later, continue to label confidence and separate confirmed recollections from speculation.）
