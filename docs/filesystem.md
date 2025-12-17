# File System Layout

Asgard uses a structured file system to separate permanent data from temporary
job-related data.

## $HOME
- Purpose: Source code, configuration files, final results
- Backed up
- Persistent across sessions

## /netscratch
- Purpose: Active job data, intermediate results, checkpoints
- Shared across the cluster
- Not backed up

## /fscratch
- Purpose: Low-latency temporary storage for highly distributed jobs
- Local to each compute node
- Not backed up

## /ds
- Purpose: Shared datasets
- Read-only
- Users must not write to this location
