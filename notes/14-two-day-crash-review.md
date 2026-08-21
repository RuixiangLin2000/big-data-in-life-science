# 两天冲刺复习笔记（Two-Day Crash Review Notes）

> 使用方法：先遮住括号中的英文，用中文解释概念；然后只看中文关键词，用英文完整回答。（How to use: first hide the English in parentheses and explain the concept in Chinese; then use only the Chinese keywords to produce a complete answer in English.）

## 1. 生命科学大数据与 3V（Big data in life science and the 3Vs）

大数据不仅表示“文件很大”，还表示数据的规模、类型或产生速度超出传统工具的方便处理能力，需要可扩展的存储、计算和分析方法。（Big data does not simply mean “large files”; it means that the scale, types, or generation rate of data exceed what traditional tools can handle conveniently, requiring scalable storage, computation, and analysis.）

### 体量（Volume）

体量表示数据的数量或总大小。（Volume refers to the amount or total size of data.）

- 全基因组测序会为大量样本产生海量 reads 和变异记录。（Whole-genome sequencing produces enormous collections of reads and variant records for many samples.）
- 高内涵成像会产生数百万张显微图像和数十亿个细胞级特征。（High-content imaging can produce millions of microscopy images and billions of cell-level features.）

### 多样性（Variety）

多样性表示数据具有不同来源、格式、结构和尺度。（Variety means that data have different sources, formats, structures, and scales.）

- 多组学研究同时包含基因组、转录组、蛋白质组和代谢组数据。（Multi-omics studies combine genomic, transcriptomic, proteomic, and metabolomic data.）
- 生命科学研究可能同时使用图像、序列、临床表格、传感器数据和自由文本。（Life-science research may combine images, sequences, clinical tables, sensor data, and free text.）

### 速度（Velocity）

速度表示数据产生、传输和处理的速率。（Velocity refers to the rate at which data are generated, transferred, and processed.）

- 测序仪可以连续产生新的 reads，需要及时完成质量控制和分析。（Sequencing instruments can continuously generate new reads that require timely quality control and analysis.）
- 可穿戴设备和患者监测系统会产生实时数据流。（Wearable devices and patient-monitoring systems generate real-time data streams.）

### 一句话意义（One-sentence significance）

生命科学大数据使研究者能够发现复杂模式、改善诊断和个体化治疗，但也带来存储、计算、数据质量、隐私、偏差和可复现性问题。（Big data in life science enables researchers to discover complex patterns and improve diagnosis and personalized treatment, but it also creates challenges in storage, computation, data quality, privacy, bias, and reproducibility.）

## 2. Spark 核心概念（Core Spark concepts）

### Transformation 与 Action

Transformation 从现有数据集定义一个新数据集，通常是惰性的，例如 `map`、`filter` 和 `groupByKey`。（A transformation defines a new dataset from an existing one and is normally lazy, for example `map`, `filter`, and `groupByKey`.）

Action 需要返回结果或写出数据，因此会触发计算，例如 `count`、`first`、`collect` 和 `save`。（An action must return a result or write data and therefore triggers computation, for example `count`, `first`, `collect`, and `save`.）

### 惰性求值（Lazy evaluation）

Spark 先记录 transformation 之间的依赖关系，直到遇到 action 才执行计算。（Spark records dependencies between transformations and postpones computation until it encounters an action.）

优点是 Spark 可以优化执行计划，并避免计算最终结果不需要的数据。（This allows Spark to optimize the execution plan and avoid computing data that the final result does not require.）

### Cache 与 Persist

`count()` 会触发计算，但不会自动缓存 RDD。（`count()` triggers computation but does not automatically cache the RDD.）

如果同一个 RDD 会被多次使用，应考虑 `cache()` 或 `persist()`；否则后续 action 可能重新执行 lineage。（If the same RDD will be reused, `cache()` or `persist()` should be considered; otherwise later actions may execute its lineage again.）

### Lineage 与容错（Lineage and fault tolerance）

RDD lineage 记录数据如何由原始输入和 transformations 产生。（RDD lineage records how data were produced from the original input and transformations.）

工作节点失败时，Spark 通常只在其他节点重新计算丢失的分区，而不是重新运行整个数据集。（When a worker fails, Spark normally recomputes only the lost partitions on other nodes rather than rerunning the entire dataset.）

### Shuffle

Shuffle 在节点之间重新分配数据，常见于分组、连接和按键聚合。（A shuffle redistributes data between nodes and commonly occurs during grouping, joining, and aggregation by key.）

它可能涉及网络传输、磁盘 I/O 和序列化，因此通常是昂贵步骤。（It may involve network transfer, disk I/O, and serialization, so it is often expensive.）

## 3. 云、虚拟机与容器（Cloud, virtual machines, and containers）

虚拟机通过 hypervisor 模拟硬件，每个 VM 通常运行自己的完整 guest operating system。（A virtual machine uses a hypervisor to virtualize hardware, and each VM normally runs its own complete guest operating system.）

容器在操作系统层进行隔离，通常共享宿主机内核，因此比 VM 更轻量、启动更快。（Containers isolate at the operating-system level and normally share the host kernel, making them lighter and faster to start than VMs.）

容器提高软件环境的一致性和可复现性，但容器镜像本身不能保证结果可复现；输入数据、参数、随机种子和工作流版本也必须记录。（Containers improve software-environment consistency and reproducibility, but an image alone cannot guarantee reproducible results; input data, parameters, random seeds, and workflow versions must also be recorded.）

云计算提供按需资源和弹性扩展，但仍需考虑数据传输、费用、权限、安全、隐私和供应商依赖。（Cloud computing provides on-demand resources and elastic scaling, but data transfer, cost, permissions, security, privacy, and vendor dependence must still be considered.）

## 4. 三种学习范式（Three learning paradigms）

### 监督学习（Supervised learning）

监督学习使用外部提供的标签学习输入到目标的映射，例如用带诊断标签的图像训练分类器。（Supervised learning uses externally provided labels to learn a mapping from inputs to targets, such as training a classifier on images with diagnostic labels.）

### 无监督学习（Unsupervised learning）

无监督学习没有目标标签，目的是发现数据结构，例如聚类细胞类型或用 PCA 降维。（Unsupervised learning has no target labels and seeks structure in the data, for example clustering cell types or reducing dimensionality with PCA.）

### 自监督学习（Self-supervised learning）

自监督学习不需要人工标签，而是从原始数据构造代理任务和目标。（Self-supervised learning does not require manual labels; it constructs a proxy task and targets from the raw data.）

例子包括遮盖 DNA 或蛋白质序列的一部分并预测缺失 token，以及判断两个增强图像是否来自同一样本。（Examples include masking part of a DNA or protein sequence and predicting the missing tokens, or determining whether two augmented images originate from the same sample.）

自监督预训练学习通用表示，随后可以使用少量标签完成下游任务。（Self-supervised pretraining learns general representations that can later support downstream tasks with limited labels.）

关键区别是：自监督仍然有明确的预测目标，但该目标由数据本身自动生成。（The key distinction is that self-supervised learning still has an explicit prediction target, but the target is generated automatically from the data itself.）

## 5. 欠拟合、过拟合和 Dropout（Underfitting, overfitting, and Dropout）

欠拟合表示模型没有充分学习训练数据中的模式，通常表现为训练和验证结果都差，而且两者差距较小。（Underfitting means that the model has not learned the patterns in the training data sufficiently; both training and validation performance are usually poor, with a relatively small gap.）

可能解决方法包括增加模型容量、减少过强正则化、降低 dropout rate、改善特征或训练更久。（Possible remedies include increasing model capacity, reducing excessive regularization, lowering the dropout rate, improving features, or training longer.）

过拟合表示模型很好地拟合训练数据，却不能推广到新数据；常见信号是训练损失继续下降，而验证损失开始持续上升。（Overfitting means that the model fits the training data well but does not generalize to new data; a common signal is falling training loss together with persistently rising validation loss.）

可能解决方法包括增加数据、数据增强、Dropout、权重衰减、early stopping 或简化模型。（Possible remedies include more data, augmentation, Dropout, weight decay, early stopping, or a simpler model.）

Dropout 在训练时随机关闭部分单元，以减少共同适应和过拟合。（Dropout randomly disables some units during training to reduce co-adaptation and overfitting.）

如果 Dropout 太强，它会降低有效模型容量并造成欠拟合；是否删除它必须结合训练和验证曲线判断。（If Dropout is too strong, it reduces effective model capacity and may cause underfitting; whether to remove it must be judged from both training and validation curves.）

## 6. 训练与验证曲线（Training and validation curves）

验证曲线通常比训练曲线波动更大，主要因为验证集较小，使指标估计具有更高方差。（Validation curves often fluctuate more than training curves mainly because the validation set is smaller, giving its metric estimate higher variance.）

训练指标通常对许多 mini-batch 求平均，而且模型直接优化训练目标，因此训练曲线更平滑。（Training metrics are normally averaged over many mini-batches, and the model directly optimizes the training objective, so the training curve is smoother.）

验证样本代表性不足、类别不平衡和随机性也会扩大波动。（An unrepresentative validation sample, class imbalance, and randomness can further increase fluctuations.）

观察曲线时要同时考虑方向和差距（When reading curves, consider both direction and gap）：

- 两条损失曲线都高且接近：可能欠拟合。（Both loss curves are high and close: possible underfitting.）
- 训练损失下降，验证损失先下降后持续上升：可能过拟合。（Training loss falls while validation loss falls and then rises persistently: possible overfitting.）
- 验证曲线轻微上下波动但总体稳定：不一定有问题。（The validation curve fluctuates slightly but remains stable overall: not necessarily a problem.）
- 两条曲线仍在改善：模型可能还没有训练充分。（Both curves are still improving: the model may need more training.）

## 7. MobileNetV2 代码检查（MobileNetV2 code checks）

如果代码同时使用 `weights=None` 和 `base_model.trainable = False`，主干网络的随机初始化权重会被冻结，无法学习有效特征。（If code uses both `weights=None` and `base_model.trainable = False`, the randomly initialized backbone is frozen and cannot learn useful features.）

迁移学习通常使用预训练权重并先冻结主干，然后训练新的分类头；之后可以用较小学习率进行 fine-tuning。（Transfer learning normally loads pretrained weights and initially freezes the backbone while training a new classification head; fine-tuning can follow with a smaller learning rate.）

如果 `pooling=None`，MobileNetV2 输出的是空间特征图；连接普通分类 Dense 层前通常加入 `GlobalAveragePooling2D`。（If `pooling=None`, MobileNetV2 outputs a spatial feature map; `GlobalAveragePooling2D` is normally added before a standard Dense classifier.）

还要检查输入尺寸、预处理函数、输出单元数量和 activation 是否与任务匹配。（Also check whether input size, preprocessing, the number of output units, and the activation match the task.）

## 8. 高内涵成像（High-content imaging）

高内涵成像结合自动显微成像、图像处理和定量分析，在大量条件下测量细胞表型。（High-content imaging combines automated microscopy, image processing, and quantitative analysis to measure cellular phenotypes across many conditions.）

它属于大数据，因为图像体量大、每个细胞的特征维度高，而且实验可能覆盖大量细胞、孔板、时间点和处理条件。（It is big data because image volume is large, feature dimensionality per cell is high, and experiments may cover many cells, wells, time points, and treatments.）

典型流程是图像获取、质量控制、分割、特征提取、归一化、批次效应处理、统计或机器学习分析以及验证。（A typical pipeline includes image acquisition, quality control, segmentation, feature extraction, normalization, batch-effect handling, statistical or machine-learning analysis, and validation.）

失败模式包括分割错误、照明差异、plate effect、数据泄漏和模型只学习实验批次。（Failure modes include segmentation errors, illumination differences, plate effects, data leakage, and models learning experimental batches rather than biology.）

## 9. QSAR 与虚拟筛选（QSAR and virtual screening）

QSAR 使用分子描述符或指纹预测化合物的性质或生物活性。（QSAR uses molecular descriptors or fingerprints to predict chemical properties or biological activity.）

类别不平衡时，accuracy 可能产生误导；应结合 precision、recall、PR-AUC、balanced accuracy 或 MCC。（With class imbalance, accuracy may be misleading; it should be supplemented by precision, recall, PR-AUC, balanced accuracy, or MCC.）

随机切分可能把结构非常相似的分子同时放入训练集和测试集，使结果过于乐观；scaffold split 更能检验对新化学骨架的泛化。（A random split may place highly similar molecules in both training and test sets and produce overly optimistic results; a scaffold split better tests generalization to new chemical scaffolds.）

适用域表示模型在哪一类化学空间中值得信任；对远离训练分布的分子，预测不确定性通常更高。（The applicability domain describes the region of chemical space in which the model can be trusted; uncertainty is usually higher for molecules far from the training distribution.）

虚拟筛选的高分候选仍需实验验证，模型排名不是生物活性的最终证据。（High-scoring candidates from virtual screening still require experimental validation; a model ranking is not final evidence of biological activity.）

## 10. AI 共同研究者：整合与合成（AI co-investigator: aggregation and synthesis）

信息整合是收集、筛选、比较和组织已有文献、数据库结果或多个智能体的输出。（Information aggregation collects, filters, compares, and organizes existing literature, database results, or outputs from multiple agents.）

知识合成是在整合材料之间建立联系，提出解释、假设或可检验的研究方向。（Knowledge synthesis connects the aggregated material and proposes explanations, hypotheses, or testable research directions.）

可能的实现包括检索增强生成、工具调用、多智能体分工、生成多个候选、批评与修订，以及增加推理时计算。（Possible implementations include retrieval-augmented generation, tool use, multi-agent division of labor, generating multiple candidates, critique and revision, and increased inference-time compute.）

主要风险包括幻觉、错误引用、偏差、不可复现推理和对流畅答案的过度信任。（Major risks include hallucinations, incorrect citations, bias, irreproducible reasoning, and excessive trust in fluent answers.）

因此，LLM 可以协助提出和筛选想法，但资料核查、领域判断和实验验证仍不可替代。（Therefore, an LLM can assist in generating and screening ideas, but source checking, domain judgment, and experimental validation remain indispensable.）

## 11. HPC、SLURM 与本地临时存储（HPC, SLURM, and node-local temporary storage）

HPC 集群由共享登录节点、计算节点、调度器和存储系统组成。（An HPC cluster consists of shared login nodes, compute nodes, a scheduler, and storage systems.）

计算密集型任务应提交给调度器，而不是长期运行在登录节点。（Compute-intensive jobs should be submitted to the scheduler rather than run for long periods on a login node.）

SLURM 根据申请的 CPU、内存、GPU 和运行时间安排任务；申请过少可能失败，申请过多会降低调度效率。（SLURM schedules jobs according to requested CPUs, memory, GPUs, and wall time; requesting too little may cause failure, while requesting too much reduces scheduling efficiency.）

节点本地临时存储适合高频中间 I/O。（Node-local temporary storage is suitable for intensive intermediate I/O.）

常见模式是把输入复制到本地临时目录、执行计算、再把最终结果复制回持久存储。（A common pattern is to copy inputs to node-local temporary storage, compute there, and copy final outputs back to persistent storage.）

任务结束时本地临时数据可能被删除，因此不能把唯一结果留在那里。（Node-local temporary data may be deleted when the job ends, so the only copy of a result must not be left there.）

## 12. Nextflow 与可复现工作流（Nextflow and reproducible workflows）

Nextflow 用 process 描述独立计算步骤，用 channel 在步骤之间传递数据。（Nextflow uses processes to describe independent computational steps and channels to pass data between them.）

每个 process 应明确输入、输出、命令和资源需求。（Each process should clearly define its inputs, outputs, command, and resource requirements.）

数据流模型允许满足输入条件的步骤并行执行。（The dataflow model allows steps whose inputs are ready to execute in parallel.）

工作流的优势包括自动化、失败恢复、并行化、参数化、执行记录以及与容器和调度器集成。（Workflow benefits include automation, failure recovery, parallelization, parameterization, execution records, and integration with containers and schedulers.）

可复现性需要固定软件版本、记录参数、保存配置，并避免依赖未记录的本地状态。（Reproducibility requires pinned software versions, recorded parameters, saved configuration, and avoidance of undocumented local state.）

## 13. 万能简答题结构（Reusable short-answer structure）

遇到概念题时按以下五步回答（Use the following five steps for a concept question）：

1. 给出准确的一句话定义。（Give an accurate one-sentence definition.）
2. 解释它如何工作。（Explain how it works.）
3. 给出一个生命科学例子。（Give one life-science example.）
4. 说明一个优势或意义。（State one advantage or significance.）
5. 说明一个限制、风险或失败模式。（State one limitation, risk, or failure mode.）

不要只列关键词；每一个判断都补一句“因为”。（Do not merely list keywords; support every conclusion with a sentence beginning conceptually with “because.”）

## 14. 考前自测（Pre-exam self-test）

在不看笔记的情况下回答（Answer without looking at the notes）：

1. 解释 3V，并为每个 V 给出两个生命科学例子。（Explain the 3Vs and give two life-science examples for each.）
2. 为什么 `map` 不立即计算，而 `count` 会触发计算？（Why does `map` not compute immediately while `count` triggers computation?）
3. 节点失败后，Spark 为什么不必重算整个数据集？（Why does Spark not need to recompute the entire dataset after a worker failure?）
4. 容器与 VM 的核心区别是什么？（What is the core difference between a container and a VM?）
5. 自监督学习的“标签”从哪里来？（Where do the “labels” in self-supervised learning come from?）
6. 如何从曲线区分欠拟合和过拟合？（How can underfitting and overfitting be distinguished from the curves?）
7. 为什么验证曲线可能更不稳定？（Why may a validation curve be less stable?）
8. 冻结 `weights=None` 的 MobileNetV2 有什么问题？（What is wrong with freezing a MobileNetV2 model initialized with `weights=None`?）
9. 为什么 QSAR 不能只看 accuracy？（Why is accuracy alone insufficient for QSAR?）
10. 信息整合与知识合成有什么区别？（What is the difference between information aggregation and knowledge synthesis?）

全部能在 60–90 秒内清楚回答，才算真正掌握。（You have genuinely mastered the material only when each question can be answered clearly within 60–90 seconds.）

## 综合自测题库（Comprehensive self-test bank）

完成本页复习后，使用[综合自测题与参考答案（comprehensive self-test with answers）](../exams/comprehensive-self-test-with-answers.md)进行闭卷检查。（After reviewing this page, use the [comprehensive self-test with answers](../exams/comprehensive-self-test-with-answers.md) for closed-book assessment.）
