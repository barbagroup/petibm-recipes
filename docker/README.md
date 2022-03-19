# Dockerfile for PetIBM

The present directory contains the `Dockerfile` files used to create Docker images for PetIBM.
Once built, the Docker images are pushed and shared on the DockerHub repository `barbagroup/petibm`.

## `barbagroup/petibm:0.5.3-GPU-OpenMPI-focal-devel`

Image based on Ubuntu 20.04 (Focal).
To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.3-GPU-OpenMPI-focal-devel
```

PetIBM (0.5.3) was installed along with its dependencies:

* CUDA Toolkit 11.6 (requires CUDA Driver Version >= 418.39)
* OpenMPI 3.1.4
* PETSc 3.16.5
* AmgX 2.2.0

To launch a container:

```shell
docker run -it barbagroup/petibm:0.5.3-GPU-OpenMPI-focal-devel /bin/bash
```

To launch a container with the GPU support:

```shell
docker run --gpus <devices> -it barbagroup/petibm:0.5.3-GPU-OpenMPI-focal-devel /bin/bash
```

(More details on how to specify `<devices>` can be found [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/user-guide.html#gpu-enumeration).)

To re-build the image:

```shell
docker build --tag=<your-tag> --file=Dockerfile-0.5.3-GPU-OpenMPI-focal-devel .
```

## `barbagroup/petibm:0.5.3-GPU-OpenMPI-focal`

This image is the same as `barbagroup/petibm:0.5.3-GPU-OpenMPI-focal-devel`, except it does not contain the source files and build directories.
This is intended to make the Docker image as light as possible.

To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.3-GPU-OpenMPI-focal
```

To launch a container:

```shell
docker run -it barbagroup/petibm:0.5.3-GPU-OpenMPI-focal /bin/bash
```

To launch a container with the GPU support:

```shell
docker run --gpus <devices> -it barbagroup/petibm:0.5.3-GPU-OpenMPI-focal /bin/bash
```

(More details on how to specify `<devices>` can be found [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/user-guide.html#gpu-enumeration).)

## `barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7`

PetIBM (0.5.2) was installed along with its dependencies:

* CUDA 10.1
* OpenMPI v4.0.5 (with Infiniband, UCX, Slurm, PMI, CUDA enabled)
* AmgX 919fb92
* PETSc 3.12.5
* AmgXWrapper 1a93865

The base image of this version has been changed to CentOS 7 to align with the
CentOS/Red Hat-based clusters at many HPC centers.

To build the developer-version image:

```shell
docker build --target builder --tag barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7-devel --file Dockerfile-0.5.2-GPU-OpenMPI-centos7 .
```

To build the production-version image:

```shell
docker build --target production --tag barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7 --file Dockerfile-0.5.2-GPU-OpenMPI-centos7 .
```

To pull the built images from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7
```

or

```shell
docker pull barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7-devel
```

To launch a container with the GPU support and get a Bash shell:

```shell
docker run --gpus <devices> --rm --name test -it barbagroup/petibm:0.5.2-GPU-OpenMPI-centos7 /bin/bash
```
For specifying the GPU devices in `--gpus` flags, see the [documentation here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/user-guide.html#gpu-enumeration)

If the `/bin/bash` in Docker's `run` command is absent, by default, the PetIBM image
will start a SSH server daemon listening to port 23.

## `barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial-devel`

Image based on Ubuntu 16.04 (Xenial).
To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial-devel
```

PetIBM (0.5.1) was installed along with its dependencies:

* CUDA Toolkit 10.1 (requires CUDA Driver Version >= 418.39)
* OpenMPI 3.1.4
* PETSc 3.12.2
* AmgX 2.1 (commit [cf285c1](https://github.com/NVIDIA/AMGX/tree/cf285c118726f5d1e8eb740d4936dd0bdaaf9b48))

Docker containers based on this image can run PetIBM applications on CPU and GPU.
Note that if you want to run a PetIBM application using GPUs, you have to create the container using the utility [`nvidia-docker v2`](https://github.com/NVIDIA/nvidia-docker) (instead of `docker`):

```shell
nvidia-docker run -it barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial-devel /bin/bash
```

To re-build the image locally:

```shell
docker build --tag=mypetibm:mytag --file=Dockerfile-0.5.1-GPU-OpenMPI-xenial-devel .
```

## `barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial`

This image is the same as `barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial-devel`, except it does not contain the source files and build directories.
This is intended to make the Docker image as light as possible.

To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.5.1-GPU-OpenMPI-xenial /bin/bash
```

## `barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial-devel`

Image based on Ubuntu 16.04 (Xenial).
To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial-devel
```

PetIBM (0.5.1) was installed along with its dependencies:

* CUDA Toolkit 10.1 (requires CUDA Driver Version >= 418.39)
* Intel MPI library for Linux (2017, Update 2)
* PETSc 3.12.5
* AmgX 2.1 (commit [cf285c1](https://github.com/NVIDIA/AMGX/tree/cf285c118726f5d1e8eb740d4936dd0bdaaf9b48))

Docker containers based on this image can run PetIBM applications on CPU and GPU.
Note that if you want to run a PetIBM application using GPUs, you have to create the container using the utility [`nvidia-docker v2`](https://github.com/NVIDIA/nvidia-docker) (instead of `docker`):

```shell
nvidia-docker run -it barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial-devel /bin/bash
```

To re-build the image locally:

```shell
docker build --tag=mypetibm:mytag --file=Dockerfile-0.5.1-GPU-IntelMPI-xenial-devel .
```

## `barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial`

This image is the same as `barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial-devel`, except it does not contain the source files and build directories.
This is intended to make the Docker image as light as possible.

To pull the image from DockerHub:

```shell
docker pull barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.5.1-GPU-IntelMPI-xenial /bin/bash
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
docker pull barbagroup/petibm:0.5-GPU-OpenMPI-xenial
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.5-GPU-OpenMPI-xenial /bin/bash
```

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
docker pull barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial
```

To run a container:

```shell
nvidia-docker run -it barbagroup/petibm:0.4.2-GPU-OpenMPI-xenial /bin/bash
```
