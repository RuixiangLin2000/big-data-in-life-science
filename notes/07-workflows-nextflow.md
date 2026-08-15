# 科学工作流与 Nextflow（Scientific Workflows and Nextflow）

## 中文导读（Chinese Guide）

科学工作流把任务依赖关系显式化，并支持缓存、失败重试、日志、来源追踪和独立任务并行。不同系统分别侧重消息传输、交互查询或基于文件的可复现批处理。

Nextflow 使用数据流模型：进程通过异步 Channel 交换数据。Queue Channel 发出一系列值，Value Channel 可被重复使用；Executor 可将任务映射到本地、SLURM、云或 Kubernetes。

复现记录应包含输入校验和、代码版本、参数、软件或容器版本、命令、资源申请、日志和输出校验和。常见问题包括隐藏输入、可变镜像标签、输出文件名冲突、未记录随机种子和不安全的缓存复用。

---

## 英文原文（Original English）

# Scientific Workflows and Nextflow

## Why workflows matter

Workflow systems model task dependencies, avoid recomputation, isolate partial outputs, retry failures, log provenance, and parallelize independent work. They help move a pipeline among laptops, HPC systems, and cloud platforms.

## Pipeline styles

- Queue/topic systems emphasize robust event movement.
- DataFrame systems emphasize queries and interactive analytics.
- File-based scientific workflows emphasize immutable data, caching, and recovery.

## Provenance checklist

Record input checksums, code revision, parameters, software or container versions, commands, resource requests, logs, exit status, and output checksums.

## Nextflow model

Nextflow is dataflow-oriented. Isolated processes exchange values through asynchronous channels.

```nextflow
nextflow.enable.dsl=2
params.input = 'data/*.txt'

process COUNT_LINES {
    input:
    path input_file

    output:
    tuple val(input_file.simpleName), path('count.txt')

    script:
    """
    wc -l ${input_file} > count.txt
    """
}

workflow {
    inputs = Channel.fromPath(params.input, checkIfExists: true)
    COUNT_LINES(inputs)
}
```

Queue channels emit sequences; value channels can be reused. Processes declare inputs, outputs, directives, and scripts. Operators transform channels. The `-resume` option reuses compatible cached tasks. Executors map tasks to local, SLURM, cloud, or Kubernetes environments.

## Pitfalls

- Symbolic published outputs break after deleting the work directory.
- Mutable container tags weaken reproducibility.
- Global undeclared files become hidden inputs.
- Colliding filenames overwrite results.
- Randomized tools need recorded seeds.
- Cache reuse is unsafe when dependencies are not declared.
