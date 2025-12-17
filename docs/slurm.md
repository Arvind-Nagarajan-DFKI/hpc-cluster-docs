# Slurm Job Scheduling

Slurm is the workload manager used by **Asgard** to schedule and execute jobs on
the GPU cluster. Users do not run heavy workloads directly on the login node;
instead, they submit jobs to Slurm, which allocates GPUs, CPUs, and memory in a
controlled and reproducible manner.

---

## Core Concepts

### Jobs
A **job** is a unit of work submitted to Slurm. Each job requests specific
resources such as GPUs, CPUs, memory, and runtime.

### Nodes and GPUs
- A **node** is a physical machine.
- A **GPU** is an accelerator attached to a node.
- Slurm allocates GPUs using **GRES (Generic Resources)**.

### Job ID
Each submitted job is assigned a unique **Job ID**, available inside the job as
the environment variable `$SLURM_JOB_ID`.

---

## Submitting a Job

Jobs are submitted using the `sbatch` command with a job script.

---

## Example Job Script

```bash
#!/bin/bash

#SBATCH --job-name=asgard-train
#SBATCH --gres=gpu:1
#SBATCH --cpus-per-task=4
#SBATCH --mem=16G
#SBATCH --time=01:00:00
#SBATCH --output=logs/%x-%j.out

# Create a job-specific working directory
JOB_DIR=/netscratch/$USER/job_$SLURM_JOB_ID
mkdir -p "$JOB_DIR"
cd "$JOB_DIR"

# Run training inside the allocated resources
python train.py

```