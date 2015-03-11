# Docker for Solaris 11.2

What is all the hype about Docker? Is it something like Solaris Zones? Reading some stuff on the web, it seems that _Docker_ is actualy popular not because of the container technology (that exits form more than a decade),
but mostly because of its clever API and CLI. (see https://www.docker.com/tryit/)

This is a quick an dirty naive implementation of a small subset of Docker CLI on Solaris 11.2. About 250 lines of BASH scripting using _Solaris Zone_ and _Virtual VNIC_ as backend.


## Open a terminal (user root) on a Solaris 11.2 system

If you don't have Solaris (best Entreprise OS in the World :). You can install it quickly in a sandbox.

- Install VirtualBox (https://www.virtualbox.org/wiki/Downloads)
- Download Solaris 11.2 image (http://www.oracle.com/technetwork/server-storage/solaris11/downloads/vm-templates-2245495.html)
- Full procedure (http://www.oracle.com/technetwork/systems/hands-on-labs/s11-vbox-install-1408628.html)

## Install docker4solaris (clone git repository)

The first invocation will set up networking for Doker and create the _learn/tutorial_ image in a local repository. All containers will have a vnic connected to an internal switch (_docketint0_). DHCP and NAT (_ipfilter_) running in the global zone provide access to external world.

	pkg install git
	git clone https://github.com/maduma/docker4solaris.git
	export PATH=$PATH:$PWD/docker4solaris/bin
	docker
	
## Follow the docker tutorial

	docker version
	docker search tutorial
	docker pull learn/tutorial
	docker run learn/tutorial echo "Hello World"
	docker run learn/tutorial ping www.google.com
	docker run learn/tutorial pkg install apache-22
	docker ps -l
	docker commit CONTAINER learn/apache-22
	docker images
	docker run learn/apache-22 /usr/apache2/2.2/bin/apachectl -M
	docker inspect CONTAINER
	docker push learn/apache-22
	
## Clean all things

	docker-clean
	
