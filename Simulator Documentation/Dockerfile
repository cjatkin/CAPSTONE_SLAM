# syntax=docker/dockerfile:1

FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && apt-get install -y \
	git \
	&& rm -rf /var/lib/apt/lists/*

# Install ArduPilot
RUN git clone –recurse-submodules https://github.com/ArduPilot/ardupilot.git
RUN ardupilot/Tools/environment_install/install-prereqs-ubuntu.sh -y
RUN . ~/.profile

# Build ArduCopter
CMD ./waf configure --board sitl
CMD ./waf copter
