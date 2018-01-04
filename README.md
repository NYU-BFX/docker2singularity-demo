# `docker2singularity` Demo

This demo will show you how to convert a Docker container into a Singularity container, starting from a Dockerfile.

__NOTE:__ Workflow designed for macOS

- create the demo Docker container for conversion to Singularity

```bash
make docker
```

- make sure the demo Docker is working

```bash
make docker-test
# FastQC v0.11.5
```

output:
```
docker run --rm -t stevekm/fastqc --version
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
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
FastQC v0.11.5
Connection to 127.0.0.1 closed.
```

- if something broke along the way, reset with:

```bash
make clean
```

# Software

Used in this workflow:

- Docker version 17.09.1-ce, build 19e2cf6
- Vagrant 2.0.1
- macOS Sierra 10.12
