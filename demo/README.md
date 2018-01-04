# usage

- create the demo Docker container for conversion to Singularity

```bash
make docker
```

- make sure the demo Docker is working

```bash
make docker-test
# FastQC v0.11.5
```

- setup the docker2singularity container and convert the demo Docker to Singularity

```bash
make docker2singularity
```

- load the demo converted Singularity container

```
make vagrant
```
