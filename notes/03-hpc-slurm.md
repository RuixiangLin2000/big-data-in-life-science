# 高性能计算与 SLURM（High-Performance Computing and SLURM）

## 集群模型（Cluster model）

集群包括登录节点、计算节点、共享存储、节点本地存储和调度器。登录节点用于轻量准备，繁重任务应交给调度作业。（A cluster contains login nodes, compute nodes, shared storage, node-local storage, and a scheduler. Login nodes are for lightweight preparation; heavy tasks belong in scheduled jobs.）

## 资源申请（Resource requests）

作业通常需要指定账户或配额、最长运行时间、CPU 核数、内存、可选 GPU 以及输出和错误文件。（A job normally specifies: account or allocation; wall-clock time; CPU cores; memory; optional GPU resources; and output and error files.）

资源应足够但不过度申请：申请不足会导致失败，申请过多会增加排队时间并浪费资源。（Request enough resources without excessive over-allocation. Under-requesting causes failures; over-requesting can increase queue time and waste capacity.）

## 批处理脚本示例（Example batch script）

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

应使用当前课程或计算中心提供的配额标识，不要硬编码旧课件中的标识。（Use the allocation identifier supplied by the current course or computing center rather than hard-coding an identifier from old slides.）

## 核心命令（Core commands）

```bash
sbatch job.sh
squeue -u "$USER"
scancel JOB_ID
sacct -j JOB_ID
```

软件模块可以在不全局修改系统的情况下提供已安装应用。（Software modules expose installed applications without modifying the system globally.）

## 节点本地临时存储（Node-local temporary storage）

节点本地存储速度更快，但它是临时的。安全流程是：复制输入到本地存储、在那里计算、作业结束前把验证后的输出复制回去。（Node-local scratch is faster than shared storage but is temporary. A safe pattern is: copy inputs from persistent storage to job-local storage; compute there; and copy verified outputs back before the job ends.）

不要假设临时数据会在作业结束后保留。（Never assume temporary data survives job completion.）

## 扩展策略（Scaling strategy）

- 对独立样本使用作业数组。（Use job arrays for independent samples.）
- 仅在工具支持时使用多线程。（Use multithreading only when the tool supports it.）
- 用代表性样本估算内存。（Estimate memory from representative samples.）
- 扩展到完整数据集前先进行基准测试。（Benchmark before scaling to the full dataset.）
- 保留日志、命令、版本和校验和。（Keep logs, commands, versions, and checksums for reproducibility.）
