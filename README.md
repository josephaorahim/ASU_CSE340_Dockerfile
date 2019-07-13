# How to Execute and Debug C/C++ Assignments in a CLI



- [ ] Required
- [ ] Who is this for?
- [ ] Why I used Docker
- [ ] Show you my Dockerfile
- [ ] How to map your host drive to the container for access
- [ ] Show you how to run a container


## Required
1. Text editor
2. Docker


## Who is this for?
This for anyone who wants to execute and debug code (specifically C/C++ but you can change the Dockerfile to include the package to debug your preferred language) using a text editor and Docker.



## Why Docker for my ASU assignments?
I couldn't find a text editor or IDE that I could debug my C/C++ assignments.



## Here's the Dockerfile

A Dockerfile is used to create an image and then image is used to run a container.

In your project directory, take the following contents and put them in a file called ```Dockerfile```.


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

This Dockerfile uses the latest version of Ubuntu, sets the WORKDIR to the path you would like the container to start at, and gets some tools for us to work within the container.

In even simpler terms, these following lines of code will allow you to build an image that will be based on Ubuntu (latest version), that will start in a path specified in WORKDIR and already have build-essentials, gdb, and vim installed.





## Build the image
Now that we have a Dockerfile, we can build an image. You can do this by following the documentation at Docker [ HERE ](https://docs.docker.com/develop/develop-images/baseimages/)

OR

You can do what I did and use Visual Studio Code. There is a Docker plugin that allows you to right click on the Dockerfile, which will then prompt you for a name then builds the image for you. 

Now we just need share our project files between the host machine and Docker.

## Mapping your host drive

The volume flag is used to map a host directory to the Docker container so that you can access your project and make changes to it.

```
-v <host_dir>:<container_dir>
```

A shortcut is to ```cd``` into your project and execute
```
-v ./:<container_dir>
```


## Running a Container!


Here are some examples of how to run your container to execute and debug your code!
##### For Mac
```
docker run -it --rm -v ./:<container_dir> <image_name>
```

##### For PC
```
docker run -it --rm -v ./:<container_dir> <image_name>
```

After running the above command to run your container, you should be able to execute and debug the code in the CLI.

**Note: to debug you must use the flag --privileged**

