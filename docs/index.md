# Asgard GPU Cluster

Asgard is a small-scale GPU cluster prototype designed for reproducible,
containerized machine learning and high-performance workloads.

The system combines:
- Slurm for job scheduling
- Enroot and Pyxis for containerized execution
- A structured file system for data management
- Grafana for monitoring GPU usage and system health

This documentation explains both **how to use** the cluster and **how it is built**.

Asgard facts:
- 4 GPUs (NVIDIA RTX Pro 6000 Server)
- AMD Epic Turin CPU (96 CPU Cores)
- 1.5 TiB RAM
- 480GB x 2 SSD
- 3TB x 4 HDD NVMe RAID0
- Slurm Workload Manager
- Enroot container environments
- Grafana monitoring suite