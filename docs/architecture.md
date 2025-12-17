# System Architecture

## What is a Compute Node?

A compute node is a physical machine that provides CPUs, GPUs, memory, and storage
for running jobs. In the current prototype, Asgard consists of a single node
equipped with NVIDIA GPUs.

## Core Components

- **Slurm**: Schedules jobs and allocates GPUs and CPUs
- **Enroot**: Provides lightweight, rootless containers
- **Pyxis**: Integrates Enroot directly into Slurm jobs
- **File System**: Separates permanent data from temporary job data
- **Grafana**: Visualizes system and GPU metrics

## Execution Flow

1. User submits a Slurm job
2. Slurm allocates GPUs and CPUs
3. Pyxis launches the job inside an Enroot container
4. The job reads/writes data using the cluster file system
5. Metrics are collected and visualized in Grafana
