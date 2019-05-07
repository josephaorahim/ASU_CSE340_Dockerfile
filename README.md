# Dockerfile for ASU CSE340 projects
Dockerfile I used at ASU to help me with projects/assignments. For example, in CSE340 I used this Dockerfile to have access to tools such as GDB to debug my code and make to add a bit of automation to my project.

This Dockerfile uses the latest version of Ubuntu, sets the WORKDIR to the path you would like the container to start at, and gets some tools for us to work within the container.



##Dockerfile

```// BASE IMAGE
FROM ubuntu:latest

// will copy the current host (the ".") dir contents to the container dir (I would use -v volume flag, see below)
// COPY . /container_dir

// container will start with workdir
WORKDIR /project3/"Provided Code" 

// i have to have my tools
RUN apt-get update && apt-get install -y \
    build-essential \
    gdb \
    vim
    ```


