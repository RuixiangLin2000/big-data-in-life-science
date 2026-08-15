# 存储、传输、Spark 与 QSAR（Storage, Transfer, Spark, and QSAR）

## 可靠的数据传输（Reliable data transfer）

- **SFTP：** 基于 SSH 的安全交互式文件传输。（**SFTP:** secure interactive file transfer over SSH.）
- **rsync：** 高效同步，可恢复传输并只复制变化的数据块。（**rsync:** efficient synchronization; can resume and transfer only changed blocks.）
- **wget/curl：** 从 Web 服务器获取资源。（**wget/curl:** retrieve resources from web servers.）
- **scp：** 简单的加密复制，但灵活性低于现代替代工具。（**scp:** simple encrypted copy, but less flexible than modern alternatives.）
- **FTP：** 传统且不安全，除非被安全机制封装。（**FTP:** legacy and insecure unless wrapped in a secure mechanism.）

大文件应尽量使用发布方提供的校验和进行验证。（Always verify large transfers with a published checksum when available.）

```bash
sha256sum large-file
rsync -avP source/ destination/
```

## 压缩与访问模式（Compression and access patterns）

压缩降低存储与传输成本；格式选择取决于顺序读取还是随机访问。归档负责打包多个文件，压缩负责变换字节流，两者相关但不同。（Compression reduces storage and transfer cost. Format choice depends on whether data are consumed sequentially or require random access. Archives package multiple files; compression transforms the byte stream. These are related but distinct operations.）

## 存储层级（Storage hierarchy）

- 内存：最快且易失（Memory: fastest and volatile）
- 节点本地磁盘：快速、临时（Node-local disk: fast, temporary）
- 共享并行文件系统：持久且跨节点可用（Shared parallel filesystem: persistent and accessible across nodes）
- 对象存储：可扩展、面向 API、常见于云环境（Object storage: scalable, API-oriented, common in cloud environments）
- 归档存储：成本低但提取较慢（Archival storage: inexpensive but slower to retrieve）

大量小文件可能使元数据服务过载，应在合适时进行合并或使用容器格式。（Many small files can overload metadata services; consolidate or choose a suitable container format when appropriate.）

## MapReduce 直觉（MapReduce intuition）

Map 把记录转换为键值对，Shuffle 按相同键分组，Reduce 合并值。记录可以独立处理且网络传输可控时，这一模式易于扩展。（Map transforms records into key-value pairs. Shuffle groups equal keys. Reduce combines values. The pattern scales when records can be processed independently and network movement remains manageable.）

## Apache Spark（Apache Spark）

Spark 将分布式转换表示为计算图，并延迟执行直到 Action 需要结果。它支持弹性分区数据集、DataFrame、SQL、缓存和分布式机器学习。（Spark represents distributed transformations as a directed computation graph and delays execution until an action requires a result. It supports resilient partitioned datasets, DataFrames, SQL-style operations, caching, and distributed machine learning.）

只有当数据或计算真正需要集群时才使用 Spark；较小数据集使用本地 DataFrame 引擎通常更简单、更快。（Use Spark when data or computation genuinely require a cluster. For smaller datasets, local dataframe engines can be simpler and faster.）

## QSAR 联系（QSAR connection）

定量构效关系把分子描述符与生物活性联系起来。（Quantitative structure-activity relationship modeling links molecular descriptors to biological activity.）

典型流程是标准化化学结构、计算描述符或指纹、定义任务、在无泄漏条件下划分数据、训练验证模型并检查适用域与不确定性。（Typical workflow: standardize chemical structures; calculate descriptors or fingerprints; define a similarity or predictive task; split data without leakage; train and validate models; and examine applicability domain and uncertainty.）

化学系列和近重复结构可能跨越随机划分产生泄漏，因此基于骨架的评估通常更现实。（Chemical series and near-duplicate structures can leak across random splits; scaffold-aware evaluation is often more realistic.）
