# 作业 2：使用 Nextflow 构建科学工作流（Assignment 2: Scientific Workflows with Nextflow）

## 中文导读（Chinese Guide）

作业分为两部分：第一部分把现有 XCMS 工作流中的峰宽、噪声和极性等值移动到配置和命令行参数；第二部分从零构建四阶段 OpenMS 工作流。

四个阶段依次为特征检测、全体特征文件对齐、特征链接和表格导出。这里重点考查 File Channel、Queue/Value Channel、重复参数输入、collect、输入输出声明、资源指令、执行配置、容器、缓存恢复和最终结果发布。

调试时应先检查 Channel 形状和生成的命令，明确某一步是按文件运行还是对完整集合运行，并避免输出冲突。公开页面不包含学生完成的 Nextflow 代码、课程路径或资源编号。

---

## 英文原文（Original English）

# Assignment 2: Scientific Workflows with Nextflow

## Goal

Practice parameterized, reproducible mass-spectrometry preprocessing in two parts:

1. Refactor an existing XCMS workflow so selected values come from configuration or command-line parameters.
2. Build an equivalent four-stage OpenMS workflow from scratch.

## Part 1: Parameterization

The original workflow contains values for peak-width limits, noise threshold, and ionization polarity. Move these values into the configuration layer and expose them as workflow parameters.

Key idea:

```text
defaults in configuration
        +
optional command-line overrides
        |
        v
process script reads params
```

The submission requirements represented in the supplied material include the modified workflow, configuration, and a record of the invocation. This repository does not publish the completed student implementation.

## Part 2: OpenMS dataflow

### Required logical stages

1. **Feature detection**
   - one mass-spectrometry input file per task
   - one reusable feature-finder parameter file
   - one feature file per input

2. **Alignment**
   - collect all feature files
   - run one alignment task across the collection
   - emit one aligned feature file per input
   - request sufficient memory

3. **Linking**
   - collect aligned feature files
   - merge them into one consensus file
   - request sufficient memory

4. **Export**
   - convert the consensus file to a table
   - clean the exported table
   - publish only the final cleaned result

## Nextflow concepts assessed

- File and value/queue channels
- Reusing a parameter input with multiple data items
- `collect` for all-at-once stages
- Constructing input and output argument lists
- Process inputs and outputs
- Resource directives
- Profiles and scheduler execution
- Containers
- Cache-aware resumption
- Publishing final outputs

## Debugging checklist

- Print or inspect constructed commands before expensive runs.
- Check that channel shapes match process declarations.
- Confirm whether a task should run per file or once per collection.
- Use unique output locations.
- Resume only when cached tasks remain valid.
- Inspect scheduler state and cancel clearly incorrect expensive runs.
- Separate workflow logic from infrastructure configuration.

Course-specific filesystem paths, allocation identifiers, and container cache locations are deliberately omitted.
