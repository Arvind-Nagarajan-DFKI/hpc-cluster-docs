# Monitoring with Grafana

Asgard uses **Grafana** to monitor the health and performance of the GPU
workstation/cluster. Monitoring provides visibility into resource usage and
helps ensure that jobs are running efficiently and correctly.

At the current stage, Grafana is used as the primary monitoring and visualization
tool.

---

## Why Monitoring Is Important

Monitoring allows administrators and users to:

- Observe GPU utilization during Slurm jobs
- Detect idle or underutilized GPUs
- Monitor system load and resource usage
- Identify potential performance bottlenecks
- Validate that allocated resources are being used as expected

Without monitoring, GPU resources can be silently wasted or misconfigured jobs
can go unnoticed.

---

## Monitoring Architecture Overview

The monitoring setup in Asgard consists of:

- **Grafana** running as a centralized visualization service
- Metrics collected from the system and GPU stack
- Dashboards displaying real-time and historical usage

Grafana provides a single interface to observe system behavior during job
execution.

---

## Grafana

Grafana is a web-based monitoring and visualization platform.

In Asgard, Grafana is used to:

- Visualize GPU utilization and memory usage
- Monitor CPU and system load
- Observe resource usage trends over time
- Support debugging of Slurm jobs and workloads

Grafana dashboards present cluster metrics in an intuitive and accessible way.

---

## Relationship to Slurm

Monitoring complements Slurm scheduling:

- **Slurm** controls *resource allocation*
- **Grafana** shows *resource utilization*

For example:
- Slurm allocates a GPU to a job
- Grafana shows whether that GPU is actively used or idle

This helps identify inefficient jobs or configuration issues.

---

## Access Policy

- Grafana dashboards are **read-only for users**
- Dashboard configuration is managed by administrators
- Users are encouraged to consult Grafana to understand job behavior

Monitoring does not allow users to interfere with other jobs or system operation.

---

## Current Scope and Future Extensions

At the current stage of Asgard:

- Grafana is deployed and operational
- Monitoring focuses on system- and GPU-level metrics
- The setup is suitable for a single-node prototype

In future phases, this setup can be extended with:
- More detailed GPU metrics
- Job-level attribution
- Alerts and notifications
- Integration with cluster-wide monitoring components

---

## Summary

Grafana provides essential visibility into the Asgard GPU environment, enabling
both administrators and users to understand how resources are used during Slurm
jobs. Even in its initial form, monitoring is a key component of a stable and
efficient GPU cluster.
