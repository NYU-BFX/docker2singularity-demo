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
# output:
# perl: warning: Setting locale failed.
# perl: warning: Please check that your locale settings:
# 	LANGUAGE = "en_US:",
# 	LC_ALL = (unset),
# 	LANG = "en_US.UTF-8"
#     are supported and installed on your system.
# perl: warning: Falling back to the standard locale ("C").
# FastQC v0.11.5
# Connection to 127.0.0.1 closed.
vagrant:
	vagrant init singularityware/singularity-2.4 && \
	sed -i '' 's|  # config.vm.synced_folder "../data", "/vagrant_data"|  config.vm.synced_folder "image", "/image"|' Vagrantfile && \
	vagrant up && \
	vagrant ssh -c 'singularity exec /image/stevekm_fastqc-*.img fastqc --version'

# remove the Vagrant files
clean-vagrant:
	rm -f Vagrantfile
	rm -rf .vagrant
