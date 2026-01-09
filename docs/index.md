# Asgard GPU Cluster

Asgard is a small-scale GPU cluster prototype designed for reproducible,
containerized machine learning and high-performance workloads.

The system combines:

- Slurm for job scheduling
- Enroot and Pyxis for containerized execution
- A structured file system for data management
- Grafana for monitoring GPU usage and system health

This documentation explains both **how to use** the cluster and **how it is built**.

---

## Asgard facts

- **GPUs:** 4 GPUs (NVIDIA RTX Pro 6000 Server)
- **CPU:** AMD Epic Turin CPU (96 CPU Cores)
- **Memory:** 1.5 TiB RAM
- **System Storage:** 480GB × 2 SSD
- **Data Storage:** 3TB × 4 HDD NVMe RAID0
- **Workload Manager:** Slurm Workload Manager
- **Containers:** Enroot container environments
- **Monitoring:** Grafana monitoring suite
