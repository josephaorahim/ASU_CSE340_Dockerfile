# How to Execute and Debug C/C++ Assignments

#### Required
### Text editor
### Docker

- [ ] Who is this for?
- [ ] Why I used Docker
- [ ] Show you my Dockerfile
- [ ] How to map your host drive to the container for access
- [ ] Show you how to run a container

## Who is this for?
This for anyone who wants to execute and debug c/c++ code 



## Why Docker for my ASU assignments?






## Dockerfile
Take the following contents and put them in a file called ```Dockerfile``` in your project directory.

This Dockerfile uses the latest version of Ubuntu, sets the WORKDIR to the path you would like the container to start at, and gets some tools for us to work within the container.

In even simpler terms, these following lines of code will allow you to build an image that will be based on Ubuntu (latest version), that will start in a path specified in WORKDIR and already have build-essentials, gdb, and vim installed.

```
// BASE IMAGE
FROM ubuntu:latest

// container will start with workdir
WORKDIR /<container_dir_you_want_to_start_with>

// i have to have my tools
RUN apt-get update && apt-get install -y \
    build-essential \
    gdb \
    vim
    
```

**Note: to use gdb you must use the flag --privileged**


## Build the image
Now that we have a Dockerfile, we can build an image (think of an image as a blueprint for the what the container should do, and the container the implementation... or the image is the class and the container is an object of that class). You can do this by following the documentation at Docker 
[ HERE ](https://docs.docker.com/develop/develop-images/baseimages/)

OR

You can do what I did and use VS Code. There is a Docker plugin that allows you to right click on the Dockerfile, which will then prompt you for a name. We're almost done, we just need to make sure that our container has access to our project.

## Mapping your host drive

Once you have the Dockerfile and the image built, you still need to access the "project" in the container somehow. We're going to do this by mapping the host project directory to a container directory. We do this with the volume flag:

```
-v <host_dir>:<container_dir>
```

Here are some examples of how to use the flag.
##### For Mac
```
docker run -it --rm -v (pwd):<container_dir> <image_name>
```

##### For PC
```
docker run -it --rm -v %cd%:<container_dir> <image_name>
```
**If you have spaces in your directories, you're going to have to have to surround the host path with quotation marks**


