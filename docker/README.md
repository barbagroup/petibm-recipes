# Dockerfile for PetIBM

The present directory contains the `Dockerfile` files used to create Docker images for PetIBM.
Once built, the Docker images are pushed and shared on the DockerHub repository `barbagroup/petibm`.

## `barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel`

Image based on Ubuntu 16.04 (Xenial).
To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel
```

PetIBM (0.4.2) was installed along with its dependencies:

* CUDA Toolkit 10.1 (requires CUDA Driver Version >= 418.39)
* OpenMPI 3.1.4
* PETSc 3.11.4
* AmgX 2.1 (commit [cf285c1](https://github.com/NVIDIA/AMGX/tree/cf285c118726f5d1e8eb740d4936dd0bdaaf9b48))

Docker containers based on this image can run PetIBM applications on CPU and GPU.
Note that if you want to run a PetIBM application using GPUs, you have to create the container using the utility [`nvidia-docker v2`](https://github.com/NVIDIA/nvidia-docker) (instead of `docker`):

```shell
nvidia-docker run -it barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel /bin/bash
```

To re-build the image locally:

```shell
docker build --tag=mypetibm:mytag --file=Dockerfile-0.4.2-GPU-OpenMPI-xenial-devel .
```

## `barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial`

This image is the same as `barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel`, except it does not contain the source files and build directories.
This is intended to make the Docker image as light as possible.

To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial-devel /bin/bash
```

## `barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel`

Image based on Ubuntu 16.04 (Xenial).
To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel
```

PetIBM (0.5) was installed along with its dependencies:

* CUDA Toolkit 10.1 (requires CUDA Driver Version >= 418.39)
* OpenMPI 3.1.4
* PETSc 3.12.2
* AmgX 2.1 (commit [cf285c1](https://github.com/NVIDIA/AMGX/tree/cf285c118726f5d1e8eb740d4936dd0bdaaf9b48))

Docker containers based on this image can run PetIBM applications on CPU and GPU.
Note that if you want to run a PetIBM application using GPUs, you have to create the container using the utility [`nvidia-docker v2`](https://github.com/NVIDIA/nvidia-docker) (instead of `docker`):

```shell
nvidia-docker run -it barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel /bin/bash
```

To re-build the image locally:

```shell
docker build --tag=mypetibm:mytag --file=Dockerfile-0.5-GPU-OpenMPI-xenial-devel .
```

## `barbagroup/petibm:0.5-GPU-OpenMPI-xenial`

This image is the same as `barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel`, except it does not contain the source files and build directories.
This is intended to make the Docker image as light as possible.

To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.5-GPU-OpenMPI-xenial-devel /bin/bash
```
