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

## Software Stack

When submitting jobs with Slurm and Pyxis, container behavior is controlled using
container-specific options. The --container-image option defines the container
environment in which the job runs, ensuring reproducible software dependencies.
The --container-mounts option exposes selected directories from the host system
inside the container, allowing access to user files, scratch space, and shared
datasets. Finally, --container-workdir specifies the directory inside the
container where execution begins, aligning the container’s context with the job’s
working directory.

```bash
--container-image=[USER@][REGISTRY#]IMAGE[:TAG]|PATH
                        [pyxis] the image to use for the container
                        filesystem. Can be either a docker image given as
                        an enroot URI, or a path to a squashfs file on the
                        remote host filesystem.

--container-mounts=SRC:DST[:FLAGS][,SRC:DST...]
                        [pyxis] bind mount[s] inside the container. Mount
                        flags are separated with "+", e.g. "ro+rprivate"

--container-workdir=PATH
```

The following command creates a container from the image /enroot/nvcr.io_nvidia_pytorch_23.12-py3.sqsh, with the current directory as workdir, and makes /netscratch, /ds, and the current directory available inside the container:

```bash
$ srun \
  --container-image=/enroot/nvcr.io_nvidia_pytorch_23.12-py3.sqsh \
  --container-workdir="`pwd`" \
  --container-mounts=/netscratch/$USER:/netscratch/$USER,/ds:/ds:ro,"`pwd`":"`pwd`" \
  [your command]
```