# 高性能计算与 SLURM（High-Performance Computing and SLURM）

## 中文导读（Chinese Guide）

计算集群通常由登录节点、计算节点、共享存储、节点本地存储和调度器组成。登录节点只用于轻量准备，耗时或高资源任务应提交给调度器。

SLURM 作业需要合理申请运行时间、CPU、内存和可选 GPU。节点本地临时存储速度快但会在作业结束后清除，因此应执行“复制输入—计算—复制并验证输出”的流程。

独立样本可使用作业数组，多线程仅适用于真正支持并行的工具。扩展到全部数据之前，应先用代表性样本测试资源需求，并保留命令、版本、参数和日志。

---

## 英文原文（Original English）

# High-Performance Computing and SLURM

## Cluster model

A cluster contains login nodes, compute nodes, shared storage, node-local storage, and a scheduler. Login nodes are for lightweight preparation; heavy tasks belong in scheduled jobs.

## Resource requests

A job normally specifies:

- account or allocation
- wall-clock time
- CPU cores
- memory
- optional GPU resources
- output and error files

Request enough resources without excessive over-allocation. Under-requesting causes failures; over-requesting can increase queue time and waste capacity.

## Example batch script

```bash
#!/usr/bin/env bash
#SBATCH --job-name=example
#SBATCH --time=01:00:00
#SBATCH --cpus-per-task=4
#SBATCH --mem=8G
#SBATCH --output=logs/%x-%j.out
#SBATCH --error=logs/%x-%j.err

set -euo pipefail
mkdir -p logs results
module load tool-name
tool-name --threads "$SLURM_CPUS_PER_TASK" --input data/input --output results/output
```

Use the allocation identifier supplied by the current course or computing center rather than hard-coding an identifier from old slides.

## Core commands

```bash
sbatch job.sh
squeue -u "$USER"
scancel JOB_ID
sacct -j JOB_ID
```

Software modules expose installed applications without modifying the system globally.

## Node-local temporary storage

Node-local scratch is faster than shared storage but is temporary. A safe pattern is:

1. Copy inputs from persistent storage to job-local storage.
2. Compute there.
3. Copy verified outputs back before the job ends.

Never assume temporary data survives job completion.

## Scaling strategy

- Use job arrays for independent samples.
- Use multithreading only when the tool supports it.
- Estimate memory from representative samples.
- Benchmark before scaling to the full dataset.
- Keep logs, commands, versions, and checksums for reproducibility.
