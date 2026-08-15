# 考试复习（Exam-Oriented Review）

本页把样题主题改写为原创复习问题，并省略所有个人或行政信息。（This page converts themes from the supplied example assessment into original study prompts and omits all personal or administrative information.）

## AI 共同科学家与测试时计算（AI co-scientist and test-time compute）

训练时扩展增加模型规模、数据或训练计算。（Training-time scaling increases model size, data, or training computation.）

测试时或推理时扩展在收到问题后给予模型更多计算。模型可以生成多个候选、分解问题、搜索推理树、批评并修订输出、检索证据、使用工具或协调多个智能体。（Test-time or inference-time scaling gives a model more computation after receiving a problem. It may generate multiple candidates, break the problem into steps, search a reasoning tree, critique and revise outputs, retrieve evidence, use tools, or coordinate several agents.）

参数可以保持不变，但系统投入更多计算来选择答案。科学应用中，这可能改善复杂推理，却不能替代资料核查与实验验证。（The parameters can remain unchanged while the system spends more effort selecting an answer. For scientific use, additional compute can improve difficult reasoning but cannot replace source checking and experimental validation.）

参见 [Seminar 阅读指南（seminar reading guide）](../seminars/ai-co-pi.md)。

## 其他重点主题（Other key topics）

- 解释大数据五个 V 如何影响模型设计、训练、验证和解释，并给出规模带来的一个优势与限制。（Explain how volume, variety, velocity, veracity, and value affect model design, training, validation, and interpretation. Give one benefit and one limitation of scale.）
- 解释节点本地临时存储及“复制输入—计算—复制输出”模式。（Explain when node-local temporary storage is useful and describe the copy-in, compute, copy-out pattern.）
- 比较安全传输、可恢复同步、Web 下载、旧协议、归档和流式压缩。（Compare secure transfer tools, resumable synchronization, web downloads, legacy transfer protocols, archives, and streaming compression.）
- 跟踪一个小型 Map、Shuffle/Group 和 Reduce 任务，并解释网络 Shuffle 的成本。（Trace a small map, group/shuffle, and reduce task. Explain why it scales and why network shuffling can become expensive.）
- 讨论基因组学中的体量、准确性、解释、隐私和工作流复现。（Discuss volume, sequencing accuracy, interpretation, privacy, and workflow reproducibility.）
- 解释云、容器、工作流、高内涵成像和深度学习正则化的优势、挑战与失败模式。（Explain advantages, challenges, and failure modes of cloud, containers, workflows, high-content imaging, and deep-learning regularization.）

## 学习方法（Study method）

每个主题都准备一个定义、一个生命科学实例、一个权衡和一个失败模式。（For every topic, prepare a definition, a life-science example, a tradeoff, and one failure mode.）
