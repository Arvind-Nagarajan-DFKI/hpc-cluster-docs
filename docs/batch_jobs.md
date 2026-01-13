## Using sbatch instead of srun

At the moment, Enroot and Pyxis are supported through srun. For batch jobs, this means writing a normal sbatch script and running your containerized workload via srun inside the script.

```bash
#!/bin/bash
# let's set the following defaults (can be overriden on commandline):
#SBATCH --job-name sbatch_test
#SBATCH --partition batch

# put your srun command with args here
srun \
  --container-image=/enroot/nvcr.io_nvidia_pytorch_23.12-py3.sqsh \
  --container-workdir="`pwd`" \
  --container-mounts=/home:/home,"`pwd`":"`pwd`" \
  echo "hello world!"
```

Then, we submit our batch job with (sbatch[script]).