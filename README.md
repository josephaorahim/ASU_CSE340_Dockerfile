# Dockerfile Guide for ASU Assignments

- [ ] Why I used Docker
- [ ] Show you the Dockerfile
- [ ] How to build the image
- [ ] How to map your host drive to the container

## Why Docker for my ASU assignments?
Dockerfile I used at ASU to help me with projects/assignments. For example, in CSE340 I used this Dockerfile to have access to tools such as GDB to debug my code and make to add a bit of automation to my project.

This Dockerfile uses the latest version of Ubuntu, sets the WORKDIR to the path you would like the container to start at, and gets some tools for us to work within the container.



## Dockerfile
Take the following contents and put them in a file called ```Dockerfile``` in your project directory.

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

**Note: to use gdb you must use the flag --privileged**


## Build the image
Now that we have a Dockerfile, we can build an image (think of an image as a blueprint for the what the container should do, and the container the implementation... or the image is the class and the container is an object of that class). You can do this by following the documentation at Docker
```https://docs.docker.com/develop/develop-images/baseimages/```

OR

You can do what I did and use VS Code, there is a Docker addon that allows you to right click on the Dockerfile then prompted for a name. Almost done, we just need to make sure that our container has access to our project.

## Mapping your host drive

This is all fine and dandy, but how do I get my stuff into the container to use all those tools????? You're going to have to map a directory from your host machine, to a directory in the container. You do this by using the flag

```
-v *hostdir* *containerdir*
```

Here are some examples of how to use the flag.
##### For Mac
```
docker run -it --rm -v (pwd):<container_dir> <image>
```

##### For PC
```
docker run -it --rm -v %cd%:<container_dir> <image>
```
**If you have spaces in your directories, you're going to have to have to surround the host path with quotation marks**
