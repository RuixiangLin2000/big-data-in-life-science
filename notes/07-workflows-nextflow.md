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
