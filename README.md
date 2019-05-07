# Dockerfile

Dockerfile I used at ASU to help me with projects/assignments. For example, in CSE340 I used this Dockerfile to have access to tools such as GDB to debug my code and make to add a bit of automation to my project.

This Dockerfile uses the latest version of Ubuntu, sets the WORKDIR to the path you would like the container to start at, and gets some tools for us to work within the container.



## Dockerfile

```
// BASE IMAGE
FROM ubuntu:latest

// container will start with workdir
WORKDIR /container_dir_you_want_to_start_with 

// i have to have my tools
RUN apt-get update && apt-get install -y \
    build-essential \
    gdb \
    vim
    
```

** Note: to use gdb you must use the flag --privileged **

### Mapping your host drive

This is all fine and dandy, but how do I get my stuff into the container to use all those tools????? You're going to have to map a directory from your host machine, to a directory in the container. You do this by using the flag

```
-v *hostdir*/*container_dir*
```

Here are some examples of how to use the flag

```
docker run -it -rm -v 

