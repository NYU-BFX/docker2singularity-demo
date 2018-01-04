SHELL:=/bin/bash

none:

# create the demo Docker container for conversion to Singularity
docker:
	docker build -t stevekm/fastqc .

# make sure the Docker is working; should output "FastQC v0.11.5"
docker-test:
	docker run --rm -t stevekm/fastqc --version

# setup the docker2singularity container and convert the demo Docker to Singularity
docker2singularity:
	docker run -v /var/run/docker.sock:/var/run/docker.sock -v ${PWD}/image:/output --privileged -t --rm singularityware/docker2singularity stevekm/fastqc

# load the demo converted Singularity container
# NOTE: macOS sed -i syntax
# NOTE: make sure there's only 1 .img file in the image dir
vagrant:
	vagrant init singularityware/singularity-2.4 && \
	sed -i '' 's|  # config.vm.synced_folder "../data", "/vagrant_data"|  config.vm.synced_folder "image", "/image"|' Vagrantfile && \
	vagrant up && \
	vagrant ssh -c 'singularity exec /image/stevekm_fastqc-*.img fastqc --version'

# remove the Vagrant files and Singularity image
clean:
	rm -f Vagrantfile
	rm -rf .vagrant
	rm -f image/stevekm_fastqc-*.img
