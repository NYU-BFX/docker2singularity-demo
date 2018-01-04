none:

# create the demo Docker container for conversion to Singularity
docker:
	docker build -t stevekm/fastqc .

# setup the docker2singularity container and convert the demo Docker to Singularity
docker2singularity:
	docker run -v /var/run/docker.sock:/var/run/docker.sock -v ${PWD}/image:/output --privileged -t --rm singularityware/docker2singularity stevekm/fastqc

# load the demo converted Singularity container
vagrant:
	vagrant init singularityware/singularity-2.4 && \
	sed -i '' 's|  # config.vm.synced_folder "../data", "/vagrant_data"|  config.vm.synced_folder "image", "/image"|' Vagrantfile && \ # macOS sed -i syntax
	vagrant up && \
	printf "please run the command:\n\nvagrant ssh\n"
