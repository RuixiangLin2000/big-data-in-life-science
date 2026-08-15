# 作业 1：在 HPC 上进行 NGS 分析（Assignment 1: NGS on HPC）

## 中文导读（Chinese Guide）

目标是构建并运行 SLURM 批处理流程，对相互独立的测序样本完成参考基因组比对和变异检测。

概念流程为：先用小数据集测试；找到匹配的参考序列和索引；分别比对每个样本；排序并索引比对文件；计算 pileup；调用变异；检查最终 BCF/VCF；最后扩展到较大数据集。

重计算必须在批处理作业中完成，并使用节点本地临时存储。作业结束前要把验证过的输出复制回持久存储，同时在日志中保留软件版本、命令和执行状态。本页不会提供可直接提交的批处理脚本。

---

## 英文原文（Original English）

# Assignment 1: NGS on HPC

## Goal

Build and run a SLURM batch workflow that processes independent sequencing samples and produces variant calls relative to a reference genome.

## Conceptual workflow

1. Start with a very small test dataset.
2. locate the indexed reference and matching FASTA index.
3. Align each sample independently.
4. Sort alignments into a binary alignment format.
5. Index each sorted alignment.
6. Compute pileups against the reference.
7. Call variants.
8. Convert or inspect the final variant representation.
9. Scale the verified procedure to the larger dataset.

## HPC requirements

- Heavy processing belongs in a batch job, not on a login node.
- Use node-local temporary storage for active computation.
- Copy inputs into temporary storage and verified outputs back to persistent storage.
- Keep samples separate.
- Load and record software modules and versions.
- Estimate time, memory, and storage before scaling.
- Preserve useful standard output for review.

## File-flow model

```text
FASTQ -> alignment -> sorted BAM -> BAM index
                           |
reference FASTA + index -> pileup -> variant call -> BCF/VCF
```

## Deliverable represented in the supplied instructions

The expected submission is the scheduler output demonstrating the executed workflow. Intermediate alignment and variant files are working data rather than the primary submission.

## Review checklist

- [ ] Small test completed before full processing
- [ ] Reference build and indices match
- [ ] Every sample processed independently
- [ ] Node-local scratch used correctly
- [ ] Outputs copied back before job completion
- [ ] Tool versions visible in the log
- [ ] No credentials or personal paths in shared material
- [ ] Commands and exit status are interpretable

This page intentionally omits course-specific paths, account values, and a ready-to-submit batch script.
