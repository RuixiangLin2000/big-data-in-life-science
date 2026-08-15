# 科学工作流与 Nextflow（Scientific Workflows and Nextflow）

## 工作流为何重要（Why workflows matter）

工作流系统可以显式描述任务依赖，避免重复计算、隔离不完整输出、重试失败任务、记录来源、并行执行独立任务，并让同一流程在笔记本电脑、HPC 和云之间迁移。（Workflow systems model task dependencies, avoid recomputation, isolate partial outputs, retry failures, log provenance, and parallelize independent work. They help move a pipeline among laptops, HPC systems, and cloud platforms.）

## 流水线类型（Pipeline styles）

- Queue/topic 系统强调可靠的事件传输。（Queue/topic systems emphasize robust event movement.）
- DataFrame 系统强调查询和交互式分析。（DataFrame systems emphasize queries and interactive analytics.）
- 基于文件的科学工作流强调不可变数据、缓存和恢复。（File-based scientific workflows emphasize immutable data, caching, and recovery.）

正确选择取决于主要问题是数据传输、查询还是可复现批处理。（The correct style depends on whether the main problem is data movement, querying, or reproducible batch computation.）

## 数据来源检查表（Provenance checklist）

记录输入校验和、代码版本、参数、软件或容器版本、命令、资源申请、日志、退出状态和输出校验和。（Record input checksums, code revision, parameters, software or container versions, commands, resource requests, logs, exit status, and output checksums.）

## Nextflow 模型（Nextflow model）

Nextflow 采用数据流模型，隔离的 Process 通过异步 Channel 交换值。（Nextflow is dataflow-oriented. Isolated processes exchange values through asynchronous channels.）

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

Queue Channel 发出一系列值，Value Channel 可重复使用；Process 声明输入、输出、指令和脚本；Operator 转换 Channel；`-resume` 可复用兼容的缓存任务；Executor 可映射到本地、SLURM、云或 Kubernetes。（Queue channels emit sequences; value channels can be reused. Processes declare inputs, outputs, directives, and scripts. Operators transform channels. The `-resume` option reuses compatible cached tasks. Executors map tasks to local, SLURM, cloud, or Kubernetes environments.）

## 常见问题（Pitfalls）

- 发布的符号链接会在删除工作目录后失效。（Symbolic published outputs break after deleting the work directory.）
- 可变容器标签会削弱可复现性。（Mutable container tags weaken reproducibility.）
- 全局未声明文件会成为隐藏输入。（Global undeclared files become hidden inputs.）
- 冲突的文件名会覆盖结果。（Colliding filenames overwrite results.）
- 随机工具需要记录种子。（Randomized tools need recorded seeds.）
- 未声明依赖变化后，缓存复用并不安全。（Cache reuse is unsafe when dependencies are not declared.）
