# 综合自测题与参考答案（Comprehensive Self-Test Questions and Answers）

> 本题库根据课程笔记、历年题型和本轮复习中的自测题整理。建议先遮住答案闭卷作答，再用参考答案校正术语和推理。（This question bank is based on the course notes, recurring historical exam formats, and the self-tests used in this review. Answer each question without looking first, then use the reference answer to correct terminology and reasoning.）

## 1. 大数据与机器学习（Big data and machine learning）

### 1.1 生命科学大数据的 3V 是什么？每项给出两个例子。（What are the 3Vs of life-science big data? Give two examples for each.）

**答案（Answer）：**体量是数据的数量或总大小，例如全基因组测序 reads 和高内涵成像图像；多样性是数据来源和格式不同，例如多组学数据以及图像、临床表格和文本；速度是数据产生与处理速率，例如测序仪持续输出和实时患者监测数据。（Volume is the amount or total size of data, such as whole-genome sequencing reads and high-content images. Variety is the diversity of sources and formats, such as multi-omics data and combinations of images, clinical tables, and text. Velocity is the rate of generation and processing, such as continuous sequencing output and real-time patient-monitoring streams.）

### 1.2 为什么“500 个样本、20,000 个特征”容易过拟合？（Why is a dataset with 500 samples and 20,000 features prone to overfitting?）

**答案（Answer）：**特征数量远大于样本数量，模型容易拟合偶然噪声而不是可推广规律。可使用特征选择、PCA、正则化、较简单模型和嵌套交叉验证，并确保降维只在训练数据上拟合。（The number of features is far larger than the number of samples, so the model can fit accidental noise rather than generalizable patterns. Possible remedies include feature selection, PCA, regularization, simpler models, and nested cross-validation, with dimensionality reduction fitted only on training data.）

### 1.3 类别不平衡时为什么 accuracy 可能误导？（Why can accuracy be misleading with imbalanced classes?）

**答案（Answer）：**如果 95% 样本属于阴性，始终预测阴性也能达到 95% accuracy，却完全找不到阳性。应结合 precision、recall/sensitivity、F1、balanced accuracy、PR-AUC 或 MCC。（If 95% of samples are negative, always predicting negative gives 95% accuracy while detecting no positives. Precision, recall/sensitivity, F1, balanced accuracy, PR-AUC, or MCC should also be considered.）

### 1.4 Precision 和 recall 的区别是什么？（What is the difference between precision and recall?）

**答案（Answer）：**Precision 表示预测为阳性的样本中有多少是真阳性；recall 表示所有真阳性中有多少被模型找到。（Precision is the fraction of predicted positives that are truly positive. Recall is the fraction of all true positives detected by the model.）

### 1.5 为什么要使用测试集或 k-fold cross-validation？（Why use a test set or k-fold cross-validation?）

**答案（Answer）：**它们用于估计模型对未见数据的泛化能力。交叉验证重复使用不同验证 folds，适合样本有限时比较模型和超参数；最终测试集应保留到模型选择完成后使用。（They estimate generalization to unseen data. Cross-validation uses different validation folds and is useful for comparing models and hyperparameters when data are limited. A final test set should remain untouched until model selection is complete.）

### 1.6 PCA 有什么作用和限制？（What are the role and limitation of PCA?）

**答案（Answer）：**PCA 把原特征投影到捕获最大方差的较少正交主成分，可降低维度、计算量和共线性。它是无监督线性方法，最大方差不一定与预测目标相关，主成分也可能难以解释。（PCA projects the original features onto fewer orthogonal components that capture the largest variance, reducing dimensionality, computation, and collinearity. It is an unsupervised linear method, so maximum variance need not be predictive and the components may be difficult to interpret.）

### 1.7 监督、无监督和自监督学习有什么区别？（How do supervised, unsupervised, and self-supervised learning differ?）

**答案（Answer）：**监督学习使用外部标签；无监督学习没有目标标签，寻找聚类或低维结构；自监督学习从数据本身自动构造代理目标，例如遮盖序列后预测缺失 token。（Supervised learning uses external labels. Unsupervised learning has no target labels and seeks structures such as clusters or low-dimensional representations. Self-supervised learning automatically constructs proxy targets from the data, such as predicting masked sequence tokens.）

### 1.8 什么是数据泄漏？（What is data leakage?）

**答案（Answer）：**训练过程意外使用了验证或测试信息，使评价结果虚高。例如在划分数据前对全部样本拟合 PCA，或让同一患者/相似 scaffold 同时进入训练和测试集。（Data leakage occurs when training accidentally uses validation or test information, producing overly optimistic evaluation. Examples include fitting PCA on all samples before splitting or placing the same patient or highly similar scaffolds in both training and test sets.）

## 2. MapReduce 与 Spark（MapReduce and Spark）

### 2.1 Map、Shuffle 和 Reduce 分别做什么？（What do Map, Shuffle, and Reduce do?）

**答案（Answer）：**Map 独立转换每条记录；Shuffle 把相同 key 的记录重新分组，可能产生昂贵网络传输；Reduce 合并每个 key 的 values。（Map independently transforms each record. Shuffle redistributes records so identical keys are grouped and may require expensive network transfer. Reduce combines the values for each key.）

### 2.2 `map(lambda x: x*x, [1,2,3,4])` 的结果是什么？（What is the result of `map(lambda x: x*x, [1,2,3,4])`?）

**答案（Answer）：**转换为列表后结果是 `[1,4,9,16]`；map 对每个元素执行平方函数。（Converted to a list, the result is `[1,4,9,16]`; map applies the square function to every element.）

### 2.3 `reduce(lambda a,b: a+b, [1,2,3,4])` 如何计算？（How is `reduce(lambda a,b: a+b, [1,2,3,4])` evaluated?）

**答案（Answer）：**依次计算 `1+2=3`、`3+3=6`、`6+4=10`，最终返回 10。（It evaluates `1+2=3`, `3+3=6`, and `6+4=10`, returning 10.）

### 2.4 课件的 Spark word count 如何工作？（How does the Spark word-count example work?）

**答案（Answer）：**`textFile` 读取行，`flatMap` 拆分单词，`map` 把单词转为 `(word,1)`，`reduceByKey` 对相同单词求和，`collect` 触发计算并将结果取回 driver。（`textFile` reads lines, `flatMap` splits words, `map` converts each word to `(word,1)`, `reduceByKey` sums identical words, and `collect` triggers execution and returns results to the driver.）

### 2.5 RDD 是什么？（What is an RDD?）

**答案（Answer）：**RDD 是 Resilient Distributed Dataset，是不可变、分区并分布在集群节点上的记录集合，能够通过重新计算丢失 partitions 实现容错。（An RDD is a Resilient Distributed Dataset: an immutable collection of records partitioned across cluster nodes, with fault tolerance through recomputation of lost partitions.）

### 2.6 Transformation 和 action 有什么区别？（What is the difference between a transformation and an action?）

**答案（Answer）：**Transformation 根据旧 RDD 描述新 RDD，通常惰性执行，例如 `map`、`filter`、`reduceByKey`；action 要求返回或保存结果并触发计算，例如 `count`、`first`、`collect`。（A transformation describes a new RDD from an old one and is normally lazy, such as `map`, `filter`, and `reduceByKey`. An action requests or saves a result and triggers computation, such as `count`, `first`, and `collect`.）

### 2.7 什么是 lazy evaluation？（What is lazy evaluation?）

**答案（Answer）：**Spark 先记录 transformations 形成执行计划，直到 action 需要结果才真正计算。这允许优化计划并避免不必要的中间计算。（Spark records transformations as an execution plan and computes only when an action requires a result. This allows plan optimization and avoids unnecessary intermediate computation.）

### 2.8 什么是 lineage？（What is lineage?）

**答案（Answer）：**Lineage 是 RDD 从原始数据经过一系列 transformations 产生的历史。Spark 用它重新计算丢失的 partitions。（Lineage is the history of transformations by which an RDD was produced from source data. Spark uses it to recompute lost partitions.）

### 2.9 Worker 失败后 Spark 如何恢复？（How does Spark recover after a worker failure?）

**答案（Answer）：**Spark 根据 lineage 在其他可用 worker 上重新计算丢失的 partitions，通常不需要重算未丢失的 partitions 或整个数据集。（Spark uses lineage to recompute the lost partitions on another available worker, normally without recomputing unaffected partitions or the entire dataset.）

### 2.10 为什么 `count()` 后的 `first()` 仍可能重新计算？（Why may `first()` recompute after `count()`?）

**答案（Answer）：**`count()` 触发计算但不会自动缓存 RDD。没有 `cache()` 或 `persist()` 时，`first()` 会重新执行获得首条记录所需的 lineage，但通常不需要物化整个 RDD。（`count()` triggers computation but does not automatically cache the RDD. Without `cache()` or `persist()`, `first()` re-executes the lineage needed for the first record, but normally does not materialize the entire RDD.）

### 2.11 为什么大型 RDD 不应随便使用 `collect()`？（Why should `collect()` be avoided on a large RDD?）

**答案（Answer）：**`collect()` 把全部结果集中到单个 driver，数据超过 driver 内存时会崩溃。可使用 `take(n)`、聚合或写入分布式存储。（`collect()` brings all results to one driver, which can crash if the data exceed driver memory. Use `take(n)`, aggregation, or distributed output instead.）

### 2.12 Spark 与 Hadoop MapReduce 的主要区别是什么？（What is the main difference between Spark and Hadoop MapReduce?）

**答案（Answer）：**Spark 可以在内存中缓存和复用中间数据，通常更适合迭代式机器学习；Hadoop MapReduce 在阶段间更多读写磁盘，适合可靠的大规模批处理且内存要求较低。（Spark can cache and reuse intermediate data in memory and is often better for iterative machine learning. Hadoop MapReduce performs more disk I/O between stages, fitting reliable large-scale batch processing with lower memory requirements.）

## 3. 文件传输与压缩工具（File-transfer and compression tools）

### 3.1 `rsync` 的主要用途是什么？（What is the main purpose of `rsync`?）

**答案（Answer）：**用于增量同步文件和目录，只传输差异并支持继续中断传输，常通过 SSH 进行远程同步。（It incrementally synchronizes files and directories, transfers only differences, supports resuming interrupted transfers, and commonly operates remotely over SSH.）

### 3.2 `wget` 的用途是什么？（What is `wget` used for?）

**答案（Answer）：**从 HTTP/HTTPS 等 Web 服务器非交互下载资源，适合脚本和公开数据下载。（It non-interactively retrieves resources from web servers such as HTTP/HTTPS and is useful in scripts and public-data downloads.）

### 3.3 FTP 和 SFTP 的区别是什么？（What is the difference between FTP and SFTP?）

**答案（Answer）：**传统 FTP 通常不加密，不适合敏感数据；SFTP 是基于 SSH 的安全文件传输协议。（Traditional FTP is normally unencrypted and unsuitable for sensitive data. SFTP is a secure file-transfer protocol based on SSH.）

### 3.4 SCP 和 `rsync` 的区别是什么？（How do SCP and `rsync` differ?）

**答案（Answer）：**SCP 提供类似远程 `cp` 的安全复制；`rsync` 更适合增量同步、目录更新和断点恢复。（SCP provides secure copying similar to remote `cp`. `rsync` is better for incremental synchronization, directory updates, and resuming transfers.）

### 3.5 Aspera 是什么？（What is Aspera?）

**答案（Answer）：**Aspera 是 IBM 的商业高速文件传输技术，适合远距离传输大型数据。（Aspera is IBM’s commercial high-speed file-transfer technology for large data over long-distance networks.）

### 3.6 gzip 和 ZIP 的区别是什么？（What is the difference between gzip and ZIP?）

**答案（Answer）：**gzip 主要压缩单个文件或数据流并支持流式解压；ZIP 可以归档多个文件和目录，并具有文件索引以访问归档内容。（gzip mainly compresses a single file or stream and supports streaming decompression. ZIP archives multiple files and directories and contains an index for accessing archive members.）

### 3.7 `zcat`、`zless` 和 `zgrep` 分别做什么？（What do `zcat`, `zless`, and `zgrep` do?）

**答案（Answer）：**`zcat` 输出 gzip 内容，`zless` 分页浏览，`zgrep` 直接在 gzip 文本中搜索。（`zcat` outputs gzip content, `zless` browses it page by page, and `zgrep` searches directly inside gzip-compressed text.）

## 4. 云、容器、虚拟机与 HPC（Cloud, containers, virtual machines, and HPC）

### 4.1 Docker 容器和 VM 的核心区别是什么？（What is the core difference between a Docker container and a VM?）

**答案（Answer）：**VM 通常包含完整 guest OS 和自己的内核；容器通常共享宿主机内核，只封装应用及依赖，因此更轻量。（A VM normally contains a complete guest OS and its own kernel. Containers normally share the host kernel and package only the application and dependencies, making them lighter.）

### 4.2 为什么容器通常比 VM 启动快？（Why do containers normally start faster than VMs?）

**答案（Answer）：**容器不需要启动完整 guest OS，只需在已有宿主机内核上启动隔离应用环境。（Containers do not need to boot a complete guest OS; they start an isolated application environment on the already running host kernel.）

### 4.3 云计算与 HPC 为什么不是对立概念？（Why are cloud computing and HPC not opposing concepts?）

**答案（Answer）：**HPC 描述高性能并行计算方式；云描述按需提供资源的服务模式。HPC 集群可以部署在机构数据中心，也可以建立在云上。（HPC describes a high-performance parallel-computing approach, whereas cloud describes an on-demand resource-delivery model. HPC clusters can exist in institutional data centres or in the cloud.）

### 4.4 云计算的一个优势和两个挑战是什么？（Give one advantage and two challenges of cloud computing.）

**答案（Answer）：**优势是 CPU、GPU 和存储可弹性扩展；挑战包括成本与数据传输管理，以及敏感生命科学数据的安全、隐私和合规。（An advantage is elastic scaling of CPU, GPU, and storage. Challenges include cost and data-transfer management, and security, privacy, and compliance for sensitive life-science data.）

### 4.5 为什么容器有助于但不能保证完全可复现？（Why do containers help but not guarantee complete reproducibility?）

**答案（Answer）：**容器固定软件及依赖环境，但还必须记录输入数据、参数、随机种子、工作流版本、参考数据库、容器 tag/digest 和硬件条件。（Containers fix software and dependencies, but input data, parameters, random seeds, workflow versions, reference databases, container tags/digests, and hardware conditions must also be recorded.）

### 4.6 云 VM 用户是否一定没有 root 权限？（Do cloud VM users necessarily lack root access?）

**答案（Answer）：**不一定。自主管理的云 VM 通常可提供管理员权限；托管服务和机构政策可能限制权限。（No. Self-managed cloud VMs commonly provide administrative access, while managed services and institutional policies may restrict it.）

### 4.7 HPC 为什么需要调度器？（Why does HPC need a scheduler?）

**答案（Answer）：**共享集群的 CPU、内存、GPU 和节点有限。SLURM 等调度器排队、分配合适资源、实施优先级和公平策略，并防止任务冲突。（CPU, memory, GPU, and nodes are limited on a shared cluster. Schedulers such as SLURM queue jobs, allocate suitable resources, apply priority and fair-use policies, and prevent job conflicts.）

### 4.8 Docker、Nextflow、SLURM 与 HPC 如何配合？（How do Docker, Nextflow, SLURM, and HPC work together?）

**答案（Answer）：**Nextflow 定义步骤和数据依赖，容器提供固定软件环境，SLURM 决定任务何时在哪个节点运行，HPC 提供计算资源。共享 HPC 常用 Apptainer/Singularity 运行 Docker-compatible images。（Nextflow defines processes and data dependencies, containers provide fixed software environments, SLURM decides when and where tasks run, and HPC provides computing resources. Shared HPC systems commonly use Apptainer/Singularity for Docker-compatible images.）

## 5. 科学工作流与 Nextflow（Scientific workflows and Nextflow）

### 5.1 Nextflow、SLURM 和分析工具分别负责什么？（What are the roles of Nextflow, SLURM, and analysis tools?）

**答案（Answer）：**Nextflow 组织 processes、数据依赖和执行逻辑；SLURM 分配 HPC 资源；BWA、bcftools 等分析工具执行具体科学计算。（Nextflow organizes processes, data dependencies, and execution logic. SLURM allocates HPC resources. Analysis tools such as BWA and bcftools perform the actual scientific computation.）

### 5.2 Process 和 channel 有什么区别？（What is the difference between a process and a channel?）

**答案（Answer）：**Process 是一个独立计算步骤，声明输入、输出和命令；channel 在 processes 之间传递数据。（A process is an independent computational step declaring inputs, outputs, and commands. A channel carries data between processes.）

### 5.3 为什么多个样本可以并行处理？（Why can multiple samples be processed in parallel?）

**答案（Answer）：**Channel 中每个独立样本可为同一 process 创建一个 task；只要输入就绪且资源可用，这些 tasks 可以同时运行。（Each independent sample in a channel can create a task for the same process. When inputs and resources are available, these tasks can run concurrently.）

### 5.4 工作流为什么提高可复现性？（Why do workflows improve reproducibility?）

**答案（Answer）：**工作流正式记录步骤、输入、输出、参数和依赖；结合版本控制、配置与容器，可重建分析逻辑和软件环境。（Workflows formally record steps, inputs, outputs, parameters, and dependencies. Combined with version control, configuration, and containers, they reconstruct analysis logic and software environments.）

### 5.5 为什么仅有工作流文件仍不能保证完全复现？（Why is a workflow file alone insufficient for complete reproducibility?）

**答案（Answer）：**还需固定输入和参考数据库版本、参数、随机种子、容器版本、配置、工作流 commit 和必要硬件信息。（Input and reference-database versions, parameters, random seeds, container versions, configuration, workflow commit, and relevant hardware information must also be fixed.）

### 5.6 静态与动态调度有什么区别？（What is the difference between static and dynamic scheduling?）

**答案（Answer）：**静态调度在运行前决定任务分配和顺序；动态调度在运行中根据依赖完成、数据产生和资源可用性安排任务。（Static scheduling determines task assignment and order before execution. Dynamic scheduling assigns tasks during execution according to completed dependencies, generated data, and resource availability.）

### 5.7 给出一个适合动态调度的生命科学例子。（Give a life-science example suited to dynamic scheduling.）

**答案（Answer）：**不同 NGS 样本完成 QC 和 alignment 的时间不同；某个样本输入准备好后即可进入下一步骤，不必等待所有样本。（Different NGS samples finish QC and alignment at different times. A sample can proceed as soon as its input is ready without waiting for every sample.）

### 5.8 `-resume` 有什么作用？（What does `-resume` do?）

**答案（Answer）：**Nextflow 使用缓存复用符合条件的成功 tasks，只重新运行失败或受代码、输入、参数变化影响的部分。通常必须保留 `work/` 和缓存信息。（Nextflow uses its cache to reuse eligible successful tasks and reruns only failed or affected tasks after code, input, or parameter changes. The `work/` directory and cache information normally must be preserved.）

### 5.9 申请 8 个 CPU 是否会自动让程序使用 8 线程？（Does requesting eight CPUs automatically make a program use eight threads?）

**答案（Answer）：**不会。调度器只预留资源，具体工具必须支持并被显式配置为使用相应线程数。（No. The scheduler only reserves resources; the tool must support and be explicitly configured to use the requested number of threads.）

## 6. 高内涵成像（High-content imaging）

### 6.1 HCI 和 HCS 有什么区别？（What is the difference between HCI and HCS?）

**答案（Answer）：**HCI 强调自动显微成像与定量表型分析；HCS 使用 HCI 在大量药物、基因或实验条件下进行筛选。（HCI emphasizes automated microscopy and quantitative phenotypic analysis. HCS uses HCI to screen large numbers of drugs, genes, or experimental conditions.）

### 6.2 为什么 HCI 属于大数据？（Why is HCI considered big data?）

**答案（Answer）：**它产生大量多通道、多视野、时间序列图像，并为大量单细胞提取数百至数千个高维特征，需要可扩展存储、自动处理和分析。（It produces large multichannel, multifield, and time-series image collections and hundreds or thousands of high-dimensional features for many individual cells, requiring scalable storage and automated processing and analysis.）

### 6.3 HCI pipeline 的主要顺序是什么？（What is the main HCI pipeline order?）

**答案（Answer）：**实验设计、图像获取、图像 QC、预处理、segmentation、特征提取、归一化/批次处理、聚合、统计或机器学习分析、实验验证。（Experimental design, image acquisition, image QC, preprocessing, segmentation, feature extraction, normalization/batch handling, aggregation, statistical or machine-learning analysis, and experimental validation.）

### 6.4 图像 QC 最重要的两个问题是什么？（What are two key image-QC problems?）

**答案（Answer）：**模糊/失焦会破坏边界并导致 segmentation 错误；照明不均会产生与生物学无关的系统性强度差异。（Blur/out-of-focus images obscure boundaries and cause segmentation errors. Uneven illumination creates systematic intensity differences unrelated to biology.）

### 6.5 为什么 segmentation 错误会影响所有下游结果？（Why do segmentation errors affect all downstream results?）

**答案（Answer）：**Area、intensity、texture、cell count 等特征均根据对象边界计算；边界错误会系统性污染这些特征和模型输入。（Features such as area, intensity, texture, and cell count are calculated from object boundaries. Incorrect boundaries systematically corrupt these features and model inputs.）

### 6.6 Metadata 为什么重要？（Why are metadata important?）

**答案（Answer）：**Metadata 把图像与 plate、well、channel、treatment、dose、batch、instrument 和时间点关联，用于追踪、归一化、批次校正、解释和复现。（Metadata link images to plate, well, channel, treatment, dose, batch, instrument, and time point, supporting tracking, normalization, batch correction, interpretation, and reproducibility.）

### 6.7 为什么不能只人工检查全部图像？（Why is manual inspection of every image unsuitable?）

**答案（Answer）：**百万级图像使人工检查不可扩展、主观且不一致。应自动 QC 全部图像，再人工检查代表性和异常样本。（Millions of images make manual inspection unscalable, subjective, and inconsistent. Automated QC should cover all images, with human review of representative and flagged cases.）

### 6.8 什么是 batch effect？（What is a batch effect?）

**答案（Answer）：**由实验日期、plate、仪器、试剂或操作者造成的系统差异，与真正处理效应无关；模型可能错误学习批次而非生物学。（A batch effect is a systematic difference caused by date, plate, instrument, reagent, or operator rather than the biological treatment. A model may learn batch identity instead of biology.）

### 6.9 Z′-factor 衡量什么？如何解释？（What does the Z′-factor measure and how is it interpreted?）

**答案（Answer）：**它根据 positive/negative controls 的均值分离与组内标准差评价 assay quality：`Z′ = 1 - 3(σp+σn)/|μp-μn|`。通常 `Z′ ≥ 0.5` 表示良好 screening window，`Z′ ≤ 0` 表示重叠严重。（It evaluates assay quality from mean separation and within-group variation of positive and negative controls: `Z′ = 1 - 3(σp+σn)/|μp-μn|`. Usually `Z′ ≥ 0.5` indicates a good screening window, while `Z′ ≤ 0` indicates severe overlap.）

## 7. 基因组学（Genomics）

### 7.1 FASTQ、BAM 和 VCF 分别保存什么？（What do FASTQ, BAM, and VCF store?）

**答案（Answer）：**FASTQ 保存 reads 和质量分数；BAM 保存压缩二进制 alignment；VCF 保存 chromosome、position、reference/alternative allele、quality 和 genotype 等 variant records。（FASTQ stores reads and quality scores. BAM stores compressed binary alignments. VCF stores variant records including chromosome, position, reference/alternative alleles, quality, and genotype.）

### 7.2 NGS variant-calling workflow 的主要顺序是什么？（What is the main NGS variant-calling workflow order?）

**答案（Answer）：**FASTQ QC、必要的 trimming、reference indexing、read alignment、SAM/BAM 转换、coordinate sorting、BAM indexing、variant calling、VCF/BCF filtering 与 annotation。（FASTQ QC, optional trimming, reference indexing, read alignment, SAM/BAM conversion, coordinate sorting, BAM indexing, variant calling, and VCF/BCF filtering and annotation.）

### 7.3 为什么 BAM 要 sort 和 index？（Why are BAM files sorted and indexed?）

**答案（Answer）：**坐标排序把 alignments 按基因组位置排列，索引允许工具快速访问指定区域而不扫描整个文件。（Coordinate sorting orders alignments by genomic position, and indexing allows rapid access to selected regions without scanning the entire file.）

### 7.4 DNA-seq 和 RNA-seq 的主要目标有什么区别？（How do the goals of DNA-seq and RNA-seq differ?）

**答案（Answer）：**DNA-seq 主要分析基因组和遗传变异；RNA-seq 主要测量基因/转录本表达和剪接。（DNA-seq mainly analyzes genomes and genetic variants. RNA-seq mainly measures gene/transcript expression and splicing.）

### 7.5 RNA-seq 为什么需要 normalization？（Why does RNA-seq require normalization?）

**答案（Answer）：**不同样本的测序深度、library size 和 RNA composition 不同，原始 counts 不能直接公平比较。（Samples differ in sequencing depth, library size, and RNA composition, so raw counts cannot be compared fairly without normalization.）

### 7.6 GWAS 的目标是什么？（What is the goal of GWAS?）

**答案（Answer）：**在大量个体中检验全基因组大量 variants 与疾病或性状之间的统计关联。（GWAS tests large numbers of variants across many individuals for statistical association with a disease or trait.）

### 7.7 GWAS 是否必须进行 whole-genome sequencing？（Does GWAS require whole-genome sequencing?）

**答案（Answer）：**不必须。GWAS 可使用 SNP arrays、imputation 或 sequencing；“genome-wide”表示在基因组范围检验大量标记。（No. GWAS may use SNP arrays, imputation, or sequencing. “Genome-wide” means testing many markers across the genome.）

### 7.8 为什么 GWAS association 不等于 causation？（Why does GWAS association not imply causation?）

**答案（Answer）：**关联 variant 可能只是与真正 causal variant 连锁，或受 population structure、confounding 和 bias 影响；需要功能实验和独立 replication。（The associated variant may merely be linked to the causal variant or affected by population structure, confounding, and bias. Functional experiments and independent replication are required.）

### 7.9 为什么 GWAS 需要 multiple-testing correction？（Why does GWAS need multiple-testing correction?）

**答案（Answer）：**同时检验数十万至数百万 variants 会产生大量偶然小 p-values，因此必须严格控制假阳性。（Testing hundreds of thousands or millions of variants creates many chance small p-values, so false positives must be controlled strictly.）

### 7.10 基因组大数据的主要准确性风险是什么？（What are major accuracy risks in genomic big data?）

**答案（Answer）：**测序错误、低覆盖度、污染、alignment 错误、variant-calling 错误、样本交换、batch effects、reference bias 和 annotation uncertainty。（Sequencing errors, low coverage, contamination, alignment errors, variant-calling errors, sample swaps, batch effects, reference bias, and annotation uncertainty.）

## 8. 深度学习（Deep learning）

### 8.1 Forward propagation、loss、backpropagation 和 optimizer 如何连接？（How are forward propagation, loss, backpropagation, and the optimizer connected?）

**答案（Answer）：**Forward propagation 使用当前参数产生预测；loss 衡量预测与目标差异；backpropagation 计算 loss 对各参数的梯度；optimizer 使用梯度更新参数以降低 loss。（Forward propagation produces predictions with current parameters. Loss measures prediction-target differences. Backpropagation computes loss gradients for each parameter. The optimizer uses gradients to update parameters and reduce loss.）

### 8.2 Loss 和 accuracy 有什么区别？（What is the difference between loss and accuracy?）

**答案（Answer）：**Accuracy 统计分类正确比例；loss 衡量预测概率与目标的差异，并提供连续训练信号。两个正确预测可有相同 accuracy 但不同 loss。（Accuracy is the proportion classified correctly. Loss measures differences between predicted probabilities and targets and provides a continuous training signal. Two correct predictions can have identical accuracy but different loss.）

### 8.3 二分类输出层如何设置？（How should a binary-classification output be configured?）

**答案（Answer）：**常用一个 sigmoid 单元和 binary cross-entropy；sigmoid 输出 0～1 概率，再用 threshold 转换为类别。（A common configuration is one sigmoid unit with binary cross-entropy. Sigmoid outputs a probability from zero to one, which is converted to a class with a threshold.）

### 8.4 Softmax 适合什么任务？（What task is softmax suited to?）

**答案（Answer）：**适合互斥多分类，把 k 个输出转换为总和为 1 的概率分布。One-hot 标签常配 categorical cross-entropy，整数标签常配 sparse categorical cross-entropy。（It is suited to mutually exclusive multiclass classification and converts k outputs into probabilities summing to one. One-hot labels commonly use categorical cross-entropy, while integer labels commonly use sparse categorical cross-entropy.）

### 8.5 Dropout 在训练中做什么？（What does Dropout do during training?）

**答案（Answer）：**随机关闭一定比例单元，降低对固定特征路径的依赖，促进稳健表示并减少过拟合；推理时通常不随机关闭。（It randomly disables a proportion of units, reducing dependence on fixed feature pathways, encouraging robust representations, and reducing overfitting. Units are normally not randomly disabled during inference.）

### 8.6 为什么过强 Dropout 会造成欠拟合？（Why can excessive Dropout cause underfitting?）

**答案（Answer）：**关闭过多单元会显著降低有效模型容量，使模型连训练数据模式都学不好，训练和验证表现都差。（Disabling too many units greatly reduces effective model capacity, preventing the model from learning even the training patterns and leaving both training and validation performance poor.）

### 8.7 如何从曲线识别过拟合？（How can overfitting be recognized from learning curves?）

**答案（Answer）：**训练 loss 持续下降、训练 accuracy 上升，而验证 loss 先降后持续升高、验证 accuracy 停滞或下降，且 train-validation gap 增大。（Training loss keeps falling and accuracy rises, while validation loss falls then persistently rises, validation accuracy stalls or falls, and the train-validation gap grows.）

### 8.8 为什么验证曲线波动往往更大？（Why do validation curves often fluctuate more?）

**答案（Answer）：**验证集通常更小，指标方差更大；类别不平衡和少数困难样本影响明显，而训练指标通常在许多 mini-batches 上平均。（The validation set is normally smaller, giving higher metric variance. Class imbalance and a few difficult samples have greater effects, while training metrics are usually averaged over many mini-batches.）

### 8.9 `weights=None` 后冻结 backbone 有什么问题？（What is wrong with freezing a backbone initialized with `weights=None`?）

**答案（Answer）：**`weights=None` 产生随机参数，`trainable=False` 禁止更新，模型会永久输出随机、无信息特征。应加载预训练权重后冻结，或允许随机 backbone 训练。（`weights=None` produces random parameters and `trainable=False` prevents updates, leaving permanently random, uninformative features. Load pretrained weights before freezing or allow the random backbone to train.）

### 8.10 为什么 batch size 不能修复错误输出层？（Why can batch size not fix an incorrect output layer?）

**答案（Answer）：**Batch size 只控制每次梯度更新使用的样本数量，不改变类别数、activation、标签编码或 loss。二分类却使用四个 softmax 输出属于任务定义不匹配。（Batch size only controls the number of samples per gradient update; it does not change class count, activation, target encoding, or loss. Using four softmax outputs for a binary task is a task-definition mismatch.）

### 8.11 Backpropagation 和 optimizer 的职责有什么区别？（How do backpropagation and the optimizer differ?）

**答案（Answer）：**Backpropagation 使用链式法则计算梯度；optimizer 决定如何根据梯度和 learning rate 更新 weights 与 biases。（Backpropagation uses the chain rule to calculate gradients. The optimizer determines how to update weights and biases using those gradients and the learning rate.）

## 9. AI 共同研究者 Seminar（AI co-investigator seminar）

### 9.1 Aggregation 和 synthesis 的核心区别是什么？（What is the core difference between aggregation and synthesis?）

**答案（Answer）：**Aggregation 收集、筛选、比较和组织已有信息；synthesis 连接不同证据，形成新解释、机制假设或可检验研究问题。（Aggregation collects, filters, compares, and organizes existing information. Synthesis connects evidence to form new interpretations, mechanistic hypotheses, or testable research questions.）

### 9.2 给出 aggregation 的生命科学例子。（Give a life-science example of aggregation.）

**答案（Answer）：**检索多篇药物耐受论文，提取涉及基因、方法、样本和结论，按 pathway 组织并标注支持、冲突和来源。（Retrieve drug-resistance papers, extract genes, methods, samples, and conclusions, and organize them by pathway with supporting, conflicting, and source information.）

### 9.3 给出 synthesis 的生命科学例子。（Give a life-science example of synthesis.）

**答案（Answer）：**连接“某基因影响代谢”“耐药细胞代谢改变”和“该基因在耐药细胞高表达”，提出该基因通过代谢促进耐药并设计 knockout 验证。（Connect evidence that a gene affects metabolism, resistant cells show metabolic changes, and the gene is highly expressed in resistant cells; propose that it promotes resistance through metabolism and design a knockout test.）

### 9.4 Test-time compute 与 training-time compute 有什么区别？（How does test-time compute differ from training-time compute?）

**答案（Answer）：**Training-time compute 用于训练或扩大模型参数；test-time compute 在模型收到具体问题后增加候选生成、检索、推理、批评、排序和修订，通常不修改参数。（Training-time compute trains or scales model parameters. Test-time compute adds candidate generation, retrieval, reasoning, critique, ranking, and revision after a trained model receives a problem, normally without changing parameters.）

### 9.5 为什么多个候选可能优于单次回答？（Why may multiple candidates outperform one response?）

**答案（Answer）：**它们扩大搜索空间、提供替代解释，并允许比较、发现错误和修订弱点，而不是受第一个想法限制。（They expand the search space, provide alternative explanations, and allow comparison, error detection, and revision rather than being limited by the first idea.）

### 9.6 Multi-agent 系统可以有哪些角色？（What roles can a multi-agent system contain?）

**答案（Answer）：**生成候选、检索证据、寻找反例、评价可行性、排序、修订和 meta-review。多个角色也可能由同一模型使用不同 prompts 实现。（Candidate generation, evidence retrieval, counterexample search, feasibility review, ranking, revision, and meta-review. Multiple roles may be implemented by one model with different prompts.）

### 9.7 为什么多个 agents 一致仍不能证明正确？（Why does agreement among agents not prove correctness?）

**答案（Answer）：**它们可能共享相同训练偏差、错误来源和错误前提，形成虚假共识；一致性不是独立科学证据。（They may share the same training biases, erroneous sources, and false premises, creating false consensus. Agreement is not independent scientific evidence.）

### 9.8 为什么 AI 假设必须实验验证？（Why must AI-generated hypotheses be experimentally validated?）

**答案（Answer）：**流畅和逻辑一致不代表事实正确。只有合理 controls、实验、统计分析、重复和独立 replication 才能把假设转化为证据。（Fluency and logical consistency do not guarantee factual correctness. Appropriate controls, experiments, statistical analysis, repetition, and independent replication are needed to turn hypotheses into evidence.）

### 9.9 使用 LLM 科研时应记录什么？（What should be recorded when using an LLM in research?）

**答案（Answer）：**模型和版本、prompts/system instructions、日期、推理参数、检索来源、工具调用、人工修改、输入数据和最终验证过程。（Model and version, prompts/system instructions, date, inference parameters, retrieved sources, tool calls, human edits, input data, and the final validation process.）

## 10. Linux、SQL 与 SLURM（Linux, SQL, and SLURM）

### 10.1 `cp`、`mv` 和 `rm` 分别做什么？（What do `cp`, `mv`, and `rm` do?）

**答案（Answer）：**`cp` 复制，`mv` 移动或重命名，`rm` 删除且通常不经过回收站。（`cp` copies, `mv` moves or renames, and `rm` deletes, normally without using a recycle bin.）

### 10.2 `>` 与 `>>` 有什么区别？（What is the difference between `>` and `>>`?）

**答案（Answer）：**`>` 把输出写入文件并覆盖原内容；`>>` 追加到文件末尾。（`>` writes output to a file and overwrites existing content. `>>` appends output to the end.）

### 10.3 Pipe `|` 有什么作用？（What does the pipe `|` do?）

**答案（Answer）：**把前一命令的标准输出作为后一命令的标准输入，例如 `zcat file.gz | head`，无需创建完整中间文件。（It passes the standard output of one command to the standard input of the next, such as `zcat file.gz | head`, without creating a complete intermediate file.）

### 10.4 SQL 中 `SELECT`、`FROM`、`WHERE` 各自负责什么？（What do `SELECT`, `FROM`, and `WHERE` do in SQL?）

**答案（Answer）：**`SELECT` 指定输出列，`FROM` 指定数据表，`WHERE` 筛选满足条件的 rows。（`SELECT` specifies output columns, `FROM` specifies tables, and `WHERE` filters rows satisfying conditions.）

### 10.5 为什么多表查询需要 join conditions？（Why do multi-table queries need join conditions?）

**答案（Answer）：**Join conditions 根据 foreign keys 与 primary keys 建立真实关系；缺少条件会产生 Cartesian product 和大量错误组合。（Join conditions establish true relationships through foreign and primary keys. Without them, a Cartesian product creates many incorrect combinations.）

### 10.6 `b.author_id = a.id` 表示什么？（What does `b.author_id = a.id` mean?）

**答案（Answer）：**把 Book 表中的 author foreign key 与 Author 表的 primary key 匹配，从而找到每本书的正确作者。（It matches the author foreign key in Book with the primary key in Author, identifying the correct author for each book.）

### 10.7 `sbatch`、`squeue` 和 `scancel` 分别做什么？（What do `sbatch`, `squeue`, and `scancel` do?）

**答案（Answer）：**`sbatch` 提交批处理脚本，`squeue` 查看排队和运行作业，`scancel` 取消指定 job ID。（`sbatch` submits a batch script, `squeue` displays queued and running jobs, and `scancel` cancels a specified job ID.）

### 10.8 为什么不能在登录节点运行大型计算？（Why should heavy computation not run on a login node?）

**答案（Answer）：**登录节点由许多用户共享，主要用于文件管理、脚本准备和提交任务；大型任务会影响所有用户，应由调度器安排到计算节点。（Login nodes are shared and intended for file management, script preparation, and job submission. Heavy jobs affect all users and should be scheduled on compute nodes.）

### 10.9 节点本地临时存储的三步模式是什么？（What is the three-step pattern for node-local temporary storage?）

**答案（Answer）：**Copy in：把输入复制到本地临时目录；compute：在那里运行高 I/O 计算；copy out：作业结束前把最终结果复制回持久存储。（Copy in: copy inputs to node-local temporary storage. Compute: run I/O-intensive work there. Copy out: return final results to persistent storage before the job ends.）

### 10.10 为什么只申请 8 CPU 不保证程序使用 8 CPU？（Why does requesting eight CPUs not guarantee their use?）

**答案（Answer）：**SLURM 只预留资源；工具必须支持多线程并通过 `--threads 8` 等参数配置，否则仍可能单线程运行。（SLURM only reserves resources. The tool must support multithreading and be configured with an option such as `--threads 8`; otherwise it may remain single-threaded.）

## 使用建议（Suggested use）

1. 第一轮只看问题，用 60–90 秒口头回答。（On the first pass, read only the question and answer aloud within 60–90 seconds.）
2. 第二轮把答不完整的题标记为“概念、推理或英文表达”问题。（On the second pass, classify incomplete answers as conceptual, reasoning, or English-expression problems.）
3. 第三轮只重做错题，并使用“定义—原理—生命科学例子—优势—限制”结构。（On the third pass, repeat only missed questions using the structure definition–mechanism–life-science example–benefit–limitation.）
4. 不要逐字背诵；必须能够解释答案中的“为什么”。（Do not memorize word for word; be able to explain why each answer is true.）
