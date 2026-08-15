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
