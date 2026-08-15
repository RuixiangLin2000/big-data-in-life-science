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
