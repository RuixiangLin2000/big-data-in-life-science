# 考试复习（Exam-Oriented Review）

## 中文导读（Chinese Guide）

本页把样题涉及的主题重组为复习框架，不包含个人或行政信息。

训练时扩展通过增加模型、数据或训练计算来改善能力；测试时或推理时扩展则在问题提出后增加计算，例如生成多个候选、分解步骤、搜索推理树、反思修订、检索资料、调用工具或协调多个智能体。参数可以保持不变，但系统会投入更多计算来筛选答案。

其他复习主题包括大数据五个维度、节点本地临时存储、数据传输与压缩、MapReduce、基因组学、云与容器、科学工作流、高内涵成像和深度学习过拟合。每个主题都应准备定义、生命科学实例、权衡和失败模式。

---

## 英文原文（Original English）

# Exam-Oriented Review

This page converts themes from the supplied example assessment into original study prompts and omits all personal or administrative information.

## AI co-scientist and test-time compute

**Training-time scaling** increases model size, data, or training computation.

**Test-time or inference-time scaling** gives a model more computation after receiving a problem. It may generate multiple candidates, break the problem into steps, search a reasoning tree, critique and revise outputs, retrieve evidence, use tools, or coordinate several agents. The parameters can remain unchanged while the system spends more effort selecting an answer.

For scientific use, additional compute can improve difficult reasoning but cannot replace source checking and experimental validation.

See the [seminar reading guide](../seminars/ai-co-pi.md).

## Other key topics

### Big data and machine learning

Explain how volume, variety, velocity, veracity, and value affect model design, training, validation, and interpretation. Give one benefit and one limitation of scale.

### HPC and temporary storage

Explain when node-local temporary storage is useful and describe the copy-in, compute, copy-out pattern. State why outputs must return to persistent storage.

### Transfer and compression

Compare secure transfer tools, resumable synchronization, web downloads, legacy transfer protocols, archives, and streaming compression.

### MapReduce

Trace a small map, group/shuffle, and reduce task. Explain why it scales and why network shuffling can become expensive.

### Genomics

Discuss volume, sequencing accuracy, interpretation, privacy, and workflow reproducibility.

### Cloud and containers

Explain an advantage and a challenge of using elastic infrastructure and containers.

### Workflows

Describe how dependency graphs, caching, logging, containers, and workflow languages support scalability and reproducibility.

### High-content imaging

Explain why automated preprocessing, normalization, feature extraction, machine learning, and rich metadata are necessary.

### Deep learning

Interpret diverging training and validation curves. Explain how dropout and other regularization methods may improve generalization.

## Study method

For every topic, prepare a definition, a life-science example, a tradeoff, and one failure mode.
