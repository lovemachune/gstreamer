# gstreamer
Intro: Use the docker to build the gstreamer in ubuntu 16.04
## Install docker
	# run the .sh in env to install the docker
	sudo ./install_docker.sh	
## Install gstreamer
	# build the dockerfile in env
	docker build -t gstreamer-python:ubuntu-16 
	# run the images(at first time)
	xhost +local:
	sudo docker run --name gstreamer-python-16 -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix gstreamer-python:ubuntu-16
## Test gstreamer
	# if you had exit and close the container
	# restart the container and go into it 
	
	# check the container id
	sudo docker ps -a  
	# start the container
	sudo docker start <container id>  
	# copy the test file from host to container
	sudo docker cp <path of the test file> <container id>:<path you want to copy to>  
	# go into the container
	sudo docker exec -it <container id> bash  
	# compile the .c file
	gcc basic-tutorial-1.c -o basic-tutorial-1 `pkg-config --cflags --libs gstreamer-1.0`  
	# execute it
	./basic-tutorial-1
# Reference
Install gstreamer :
https://github.com/jackersson/env-setup/tree/master/gst-ubuntu-16-py  
Gstreamer example :
https://gstreamer.freedesktop.org/documentation/tutorials/basic/hello-world.html?gi-language=c
