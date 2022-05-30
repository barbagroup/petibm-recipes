# Singularity recipes for PetIBM

The present directory contains the Singularity recipes used to create Singularity images for PetIBM on [Singularity Hub](https://singularity-hub.org/) (in [this collection](https://singularity-hub.org/collections/3692)).

## `0.5.4-hpcx207-cuda102`

Not added to the collection as Singularity Hub has been archived.
This image is based on the Docker image `barbagroup/petibm:0.5.4-hpcx207-cuda102`.
The basic way to build this Apptainer (the new name of Singularity; works exactly the same as Singularity) image locally is:

```
$ sudo apptainer build petibm-0.5.4-hpcx207-cuda102.sif ./Singularity.0.5.4-HPCX207-CUDA102-bionic
```

By default, Apptainer uses RAM memory for the temporary directory.
If you encounter out-of-memory, you may need to use a disk as the temporary folder by setting the environment variable:

```
$ export APPTAINER_TMPDIR=<a folder on disk>
```

If you don't have the root privilege but Apptainer is configured properly, you may be able to use fakeroot:

```
$ apptainer build --fakeroot petibm-0.5.4-hpcx207-cuda102.sif ./Singularity.0.5.4-HPCX207-CUDA102-bionic
```

## `0.5.3-gpu-openmpi-focal`

Not added to the collection as Singularity Hub has been Archived.

## `0.5.2-gpu-openmpi-centos7`

To pull the Singularity image from the collection:

```shell
singularity pull --name petibm-0.5.2_centos7.sif shub://barbagroup/petibm-recipes:0.5.2-gpu-openmpi-centos7
```

## `0.5.1-gpu-openmpi-xenial`

To pull the Singularity image from the collection:

```shell
singularity pull --name petibm-0.5.1_xenial.sif shub://barbagroup/petibm-recipes:0.5.1-gpu-openmpi-xenial
```

## `0.5-gpu-openmpi-xenial`

To pull the Singularity image from the collection:

```shell
singularity pull --name petibm-0.5_xenial.sif shub://barbagroup/petibm-recipes:0.5-gpu-openmpi-xenial
```

## `0.4.2-gpu-openmpi-xenial`

To pull the Singularity image from the collection:

```shell
singularity pull --name petibm-0.4.2_xenial.sif shub://barbagroup/petibm-recipes:0.4.2-gpu-openmpi-xenial
```
