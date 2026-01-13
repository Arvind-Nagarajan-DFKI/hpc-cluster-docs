## Resource Allocation

srun offers many options to specify what resources to allocate for your job. These are the most important ones (run srun --help for the complete list):

```bash
-n, --ntasks=ntasks         number of tasks to run
    --ntasks-per-node=n     number of tasks to invoke on each node
-N, --nodes=N               number of nodes on which to run (N = min[-max])
-c, --cpus-per-task=ncpus   number of cpus required per task
    --cpus-per-gpu=n        number of CPUs required per allocated GPU
-G, --gpus=n                count of GPUs required for the job
    --gpus-per-node=n       number of GPUs required per allocated node
    --gpus-per-task=n       number of GPUs required per spawned task
    --mem=MB                minimum amount of real memory
                            real memory required per allocated GPU
    --mem-per-cpu=MB        maximum amount of real memory per allocated
                            cpu required by the job.
                            --mem >= --mem-per-cpu if --mem is specified.
```