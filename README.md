# Docker for Solaris 11.2


What is all this hype about Docker? Is it something like Solaris Zones?
Reading some stuff on the web it seems that Docker is not popular because of the container technology (that exits form more than a decade).
But mostly because of its clever API and CLI. https://www.docker.com/tryit/

Implement a small docker subset to be able to run the docker tutorial on Solaris 11.2
About 200 lines of BASH scripting and Solaris zone management commands.



## Open a terminal (user root) on a Solaris 11.2 system

If you don't have Solaris (best Entreprise OS in the World :) , you can install it quickly in a sandbox.

Install VirtualBox (https://www.virtualbox.org/wiki/Downloads)
Download Solaris 11.2 image (http://www.oracle.com/technetwork/server-storage/solaris11/downloads/vm-templates-2245495.html)
Full procedure (http://www.oracle.com/technetwork/systems/hands-on-labs/s11-vbox-install-1408628.html)

## install docker4solaris (the first invocation will create learn/tutorial image in a local repository)

	root@solaris:~# pkg install git
	root@solaris:~# git clone https://github.com/maduma/docker4solaris.git
	root@solaris:~# export PATH=$PATH:$PWD/docker4solaris/bin
	root@solaris:~# docker version
	
## follow the tutorial on docker with those slity changed command

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
	
## clean all the things

	root@solaris:~# docker-clean
	
