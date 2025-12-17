# Containers: Enroot and Pyxis

Asgard uses **Enroot** containers to provide isolated, reproducible software
environments for GPU workloads. Containers ensure that users can install their
own dependencies without affecting the system or other users.

Enroot is integrated with Slurm through **Pyxis**, allowing containers to be
launched automatically when jobs are scheduled.

---

## Why Containers Are Used

Containers in Asgard are used to:

- Avoid dependency conflicts between users
- Ensure reproducibility of experiments
- Provide GPU access without root privileges
- Keep the host operating system stable

Users should assume that **all compute jobs run inside containers**.

---

## Container Model in Asgard

- Containers run **as the user**, not as root
- Containers share the host kernel
- GPUs are passed through automatically
- File system paths such as `$HOME` and `/netscratch` are visible inside containers

Installed software inside a container **persists across runs**.

---

## Importing a Container Image

Asgard supports importing container images directly from Docker registries such
as NVIDIA NGC.

### Example: Import a PyTorch Image

```bash
enroot import docker://nvcr.io/nvidia/pytorch:23.10-py3
```