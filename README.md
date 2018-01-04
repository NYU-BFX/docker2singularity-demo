# `docker2singularity` Demo

This demo will convert a Docker container into a Singularity container, starting from a Dockerfile.

__NOTE:__ Workflow designed for macOS with Docker and Vagrant installed, see Software notes below.

You can run the entire demo workflow with

```bash
make all
```

## Step-wise Workflow

- create the demo Docker container for conversion to Singularity

```bash
make docker
```

- make sure the demo Docker is working

```bash
make docker-test
```

output:
```
FastQC v0.11.5
```

- setup the docker2singularity container and convert the demo Docker to Singularity

```bash
make docker2singularity
```

- load and test the converted Singularity container in Vagrant

```bash
make vagrant
```

output:
```
...
...
FastQC v0.11.5
Connection to 127.0.0.1 closed.
```

- if something broke along the way, reset with:

```bash
make clean
```

# Software

Tested with:

- Docker version 17.09.1-ce, build 19e2cf6

- Vagrant 2.0.1 (see installation notes in `install_vagrant.md`)

- macOS Sierra 10.12
