# 存储、Spark 与 QSAR（Storage, Spark, and QSAR）

## 中文导读（Chinese Guide）

可靠的数据传输可使用 SFTP、rsync 和 Web 下载工具；大文件应使用校验和验证完整性。压缩负责缩小字节流，归档负责把多个文件打包，两者不是同一概念。

存储层级包括内存、节点本地磁盘、共享并行文件系统、对象存储和归档存储。大量小文件可能造成元数据瓶颈。

MapReduce 将记录映射为键值对、按键分组并聚合。Spark 通过分区、延迟执行、DataFrame 和缓存支持分布式分析，但只有在数据或计算确实超过单机能力时才值得使用。

QSAR 将分子描述符与生物活性联系起来。应防止重复结构和同一化学系列泄漏到训练集与测试集两侧，并关注适用域和不确定性。

---

## 英文原文（Original English）

# Storage, Transfer, Spark, and QSAR

## Reliable data transfer

- **SFTP:** secure interactive file transfer over SSH.
- **rsync:** efficient synchronization; can resume and transfer only changed blocks.
- **wget/curl:** retrieve resources from web servers.
- **scp:** simple encrypted copy, but less flexible than modern alternatives.
- **FTP:** legacy and insecure unless wrapped in a secure mechanism.

Always verify large transfers with a published checksum when available.

```bash
sha256sum large-file
rsync -avP source/ destination/
```

## Compression and access patterns

Compression reduces storage and transfer cost. Format choice depends on whether data are consumed sequentially or require random access. Archives package multiple files; compression transforms the byte stream. These are related but distinct operations.

## Storage hierarchy

- Memory: fastest and volatile
- Node-local disk: fast, temporary
- Shared parallel filesystem: persistent and accessible across nodes
- Object storage: scalable, API-oriented, common in cloud environments
- Archival storage: inexpensive but slower to retrieve

Many small files can overload metadata services; consolidate or choose a suitable container format when appropriate.

## MapReduce intuition

Map transforms records into key-value pairs. Shuffle groups equal keys. Reduce combines values. The pattern scales when records can be processed independently and network movement remains manageable.

## Apache Spark

Spark represents distributed transformations as a directed computation graph and delays execution until an action requires a result. It supports resilient partitioned datasets, DataFrames, SQL-style operations, caching, and distributed machine learning.

Use Spark when data or computation genuinely require a cluster. For smaller datasets, local dataframe engines can be simpler and faster.

## QSAR connection

Quantitative structure-activity relationship modeling links molecular descriptors to biological activity.

Typical workflow:

1. Standardize chemical structures.
2. Calculate descriptors or fingerprints.
3. Define a similarity or predictive task.
4. Split data without leakage.
5. Train and validate models.
6. examine applicability domain and uncertainty.

Chemical series and near-duplicate structures can leak across random splits; scaffold-aware evaluation is often more realistic.
