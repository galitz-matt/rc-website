+++
categories = ["userinfo"]
type = "rivanna"
date = "2023-05-30T00:00:00-05:00"
tags = [
    "hpc","rivanna","parallel-computing","software","containers","singularity"
]
draft = true
title = "NVIDIA DGX BasePOD™"
description = ""
author = "RC Staff"

+++

# Introducing the NVIDIA DGX BasePOD™

The NVIDIA DGX BasePOD™ on Rivanna, hereafter referred to as the POD, is comprised of:
- 10 DGX A100 nodes
- 8 A100 GPU devices and 2 TB local node memory (per node)
- 80 GB GPU memory (per GPU device)

Compared to the regular GPU nodes, the POD contains **advanced features** such as:
- NVLink for fast multi-GPU communication
- GPUDirect RDMA Peer Memory for fast multi-node multi-GPU communication
- GPUDirect Storage with 200 TB IBM ESS3200 (NVMe) SpectrumScale storage array

which makes it ideal for the following types of jobs:
- The job needs multiple GPUs on a single node or even multiple nodes.
- The job (can be single- or multi-GPU) is I/O intensive.
- The job (can be single- or multi-GPU) requires more than 40 GB GPU memory. (The non-POD nodes with the highest GPU memory are the regular A100 nodes with 40 GB GPU memory.)

Detailed specs can be found in the [official document](https://docs.nvidia.com/dgx-basepod-reference-architecture-dgx-a100-and-dgx-h100.pdf) (Chapter 3.1).

# Accessing the POD

The POD nodes are contained in the `gpu` partition with a specific Slurm constraint.

## Slurm script

```bash
#SBATCH -p gpu
#SBATCH --gres=gpu:a100:X # replace X with the number of GPUs per node
#SBATCH -C gpupod
```

## Open OnDemand

In “Optional: Slurm Option” write:
```
-C gpupod
```

## Remarks
1. Before running on multiple nodes, please make sure the job can scale well to 8 GPUs on a single node.
1. Multi-node jobs on the POD should request all GPUs on the nodes, i.e. `--gres=gpu:a100:8`.
1. You may have already used the POD by simply requesting an A100 node without the constraint, since 10 out of the total 12 A100 nodes are POD nodes.
1. As we expand our infrastructure, there could be changes to the Slurm directives and job resource limitations in the future. Please keep an eye out for our announcements and documentation.

# Usage examples

## Deep learning

We will be migrating toward NVIDIA’s [NGC containers](https://ngc.nvidia.com/) for deep learning frameworks such as PyTorch and TensorFlow, as they have been heavily optimized to achieve excellent multi-GPU performance. These containers have not yet been installed as modules but can be accessed under `/share/resources/containers/singularity`:

- `pytorch_23.03-py3.sif` (PyTorch 2.0.0)
- `tensorflow_23.03-tf1-py3.sif` (TensorFlow 1.15.5)
- `tensorflow_23.03-tf2-py3.sif` (TensorFlow 2.11.0)

(NGC has their own versioning scheme.)

The singularity command is of the form:

```bash
singularity run --nv /path/to/sif python myscript.py
```

{{< alert-green >}} **Warning:** Distributed training is not automatic! Your code must be parallelizable. If you are not familiar with this concept, please visit: [TensorFlow distributed training](https://www.tensorflow.org/guide/distributed_training), [PyTorch DDP](https://pytorch.org/docs/stable/notes/ddp.html)
{{< /alert-green >}}

## MPI codes

Please check the manual of your code regarding the relationship between the number of MPI ranks and the number of GPUs. For computational chemistry codes (e.g. VASP, QuantumEspresso, LAMMPS) the two are oftentimes equal, e.g.

```bash
#SBATCH --gres=gpu:a100:8
#SBATCH --ntasks-per-node=8
```

If you are building your own code, please load the modules `nvhpc` and `cuda` which provide NVIDIA compilers and CUDA libraries. **The compute capability of the POD A100 is 8.0.**

For documentation and demos, refer to the “Resources” section at the bottom of [this page](https://developer.nvidia.com/hpc-sdk).

## GPU-enabled modules

A complete list of GPU-enabled modules on Rivanna can be found [here](https://www.rc.virginia.edu/userinfo/rivanna/software/gpu/). Please refer to their respective pages and/or module load messages (if any) for usage instructions.