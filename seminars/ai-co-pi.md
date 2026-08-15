# Seminar：AI 会成为共同课题负责人吗？（Will AI Become Our Co-PI?）

## 中文导读（Chinese Guide）

这篇观点文章区分了两类科研工作：聚合型研究侧重文献筛选、数据提取和证据整理；综合创新型研究侧重提出假设、设计实验、操纵物理系统和产生新的实证知识。

近期 AI 更适合辅助聚合任务，未来与工具和机器人连接的系统可能参与假设生成、实验优先级排序和自动化实验。推理时扩展通过在回答问题后增加搜索、候选比较、自我修订、检索和工具调用等计算来提高复杂推理质量，但更多计算并不保证真实。

讨论时应关注科学验证、黑箱与复现、临床和基因组隐私、偏差与错误传播、人类技能退化、署名、责任和实验安全。人类研究者仍必须为研究设计、数据治理、解释和纠错负责。

---

## 英文原文（Original English）

# Seminar: Will AI Become Our Co-PI?

## Session record

The supplied course notice describes a mandatory 45-minute student-led discussion scheduled for 27 May 2026. Room allocation and attendance were managed through the official learning platform and are not reproduced here.

Always verify current scheduling and participation requirements through the official course channel.

## Reading

**Will AI become our Co-PI?**  
Perspective article, 2025.  
DOI: [10.1038/s41746-025-01859-w](https://doi.org/10.1038/s41746-025-01859-w)

The paper is a perspective rather than a report of a new experiment. Its arguments should therefore be evaluated as proposals supported by selected examples, not as conclusive evidence that autonomous AI scientists already work reliably.

## Central distinction

The article separates research into two broad modes:

- **Aggregation:** literature screening, chart review, data extraction, evidence synthesis, and other repetitive information-processing tasks.
- **Synthesis:** generating hypotheses, designing experiments, manipulating physical systems, interpreting unexpected observations, and producing new empirical knowledge.

The authors argue that current language models are especially suited to parts of aggregation, while future systems connected to tools and robotics may increasingly support synthesis.

## Proposed AI roles

- Literature triage and structured evidence extraction
- Protocol planning and statistical assistance
- Cross-disciplinary pattern detection
- Hypothesis generation and iterative refinement
- Experiment prioritization
- Robotic execution of repeated experiments
- Monitoring and adapting large experimental campaigns

The strongest near-term case is assistance and automation under human supervision, not replacement of scientific responsibility.

## Test-time or inference-time scaling

Traditional scaling improves a model mainly by increasing training data, model size, or training computation.

**Inference-time scaling** spends additional computation after a question is asked. A system may:

- generate and compare several candidate solutions
- decompose a problem into intermediate steps
- search a larger reasoning tree
- critique and revise its own proposal
- call external tools or retrieve evidence
- run several agents or experiments and aggregate results

The model parameters may remain unchanged; performance can improve because the system explores more possibilities before returning an answer.

This can help scientific reasoning, but more computation does not guarantee truth. A confident error can also be elaborated or repeatedly reinforced.

## Opportunities

- Reduce repetitive workload
- Improve consistency of structured extraction
- Explore larger hypothesis spaces
- Connect literature across disciplines
- Increase experimental throughput
- Redirect human effort toward judgment and interpretation
- Document computational actions more consistently when the system is designed for provenance

## Risks and unresolved questions

### Scientific validity

AI-generated hypotheses still require empirical validation. Plausibility, novelty, and fluent explanation are not evidence.

### Reproducibility and opacity

Model internals and hidden system changes can make results difficult to reproduce. Logging prompts, model versions, retrieved sources, tools, parameters, and outputs is essential.

### Privacy and governance

Clinical and genomic data require strict access control, minimization, de-identification, and institutional approval. Public AI tools should not receive sensitive data without explicit authorization.

### Bias and error propagation

Models inherit biases and mistakes from training data and retrieved sources. Once machine-generated claims enter the literature, later systems may treat them as evidence and amplify them.

### Human skill and cognitive dependence

If automation replaces early independent reasoning, users may learn less deeply and become less able to detect errors. A safer pattern is to formulate an initial analysis before consulting AI and then compare the two.

### Credit and accountability

Responsibility cannot be delegated to a model. Human investigators remain accountable for study design, patient safety, interpretation, authorship, and correction of errors.

## Discussion prompts

1. Which aggregation tasks should be automated first, and which require human review?
2. What evidence would justify calling an AI system a scientific collaborator rather than a tool?
3. Should an opaque hypothesis be treated differently if experiments validate it?
4. How should a laboratory document AI involvement for reproducibility?
5. Can inference-time scaling produce genuinely novel science, or only search existing combinations more effectively?
6. Who is accountable when an AI-designed experiment wastes resources or causes harm?
7. Could automation increase low-quality research output instead of reducing it?
8. How should training change so that researchers gain AI skills without losing independent reasoning?
9. Which life-science domains are most and least suitable for AI-guided experimentation?
10. What minimum safeguards should exist before connecting a model to laboratory robotics?

## Suggested preparation

Bring three short points:

- one claim from the paper you find persuasive
- one assumption or limitation you would challenge
- one concrete rule for responsible AI use in a research group
