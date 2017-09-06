---
layout: post
title: Docker Tutorial
---
In this class we will be using docker as our main environment for any programming we do. This will help ensure that everybody has the same versions of software, etc. If you are using Windows go [here](#windows), Mac OS go [here](#mac), and linux go [here](#linux) for instructions on how to install docker. Once you have it installed, there are instructions for verifying your installation [here](#verify). Once you have verified your installation there is a section with a brief introduction on how docker works [here](#usage) Your first miniature homework assignment will be to submit a file to gradescope showing that you have correctly installed Docker and understand how to use it, so please follow these instructions carefully (more details on the homework assignment will come later).  

![docker logo](docker_logo.png)

# Installation

## Windows <a name="windows"></a>
1. Download the docker installer from [here](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
2. Once downloaded double click the `Docker for Windows Installer.exe` file to run the installer. 
3. Follow the instructions displayed by the installer.
4. If you run into issues, google your issue, its very likely someone has had the same issue before.
5. If you can't find a solution to your issue through a google search, try rewording your google search.
6. If you still can't find a solution, search for your issue on Piazza.
7. If you can't find it on Google or Piazza, then make a post on Piazza. 
8. If you find a solution to an issue you were having please post your issue and solution to Piazza, so other students can find help there. 

## Mac <a name="mac"></a>
1. Download the docker installer from [here](https://download.docker.com/mac/stable/Docker.dmg)
2. Once downloaded, double click the `Docker.dmg` file to start the installer.
3. Follow the instructions displayed by the installer.
4. If you run into issues, google your issue, its very likely someone has had the same issue before.
5. If you can't find a solution to your issue through a google search, try rewording your google search.
6. If you still can't find a solution, search for your issue on Piazza.
7. If you can't find it on Google or Piazza, then make a post on Piazza. 
8. If you find a solution to an issue you were having please post your issue and solution to Piazza, so other students can find help there. 

## Linux <a name="linux"></a>
If you use linux as your operating system, there are instructions on the [docker website](https://docs.docker.com/engine/installation/#server) for how to install docker on a variety of different linux distros. Installing on linux usually has far less problems than Mac or Windows so I won't include instructions here.

## Verify the installation <a name="verify"></a>
To verify that you installed docker correctly, run the following command in a terminal of your choice (if you're on Windows I would strongly recommend using git bash, but if you have a preferred terminal that works for you that's also fine): 

``` docker run hello-world```

If you correctly installed docker, this command should output the following

```

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
 https://hub.docker.com

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

```

If you didn't see the above message after running the command, first check that you typed the command correctly, then if you are on Windows or Mac make sure Docker is running. To make sure Docker is running check for a little docker logo in the notification area on Windows or in the top status bar on a Mac. The logo looks like this on Windows: ![docker status icon](https://d1q6f0aelx0por.cloudfront.net/icons/whale-x-win.png) and similar on Mac. Click on the logo and it should bring up a window that will have a green light if docker is running. If you are on Ubuntu linux run ```sudo service docker start``` to ensure that Docker is started. If you are on a different Linux distro then run the equivalent command to start a service on your distro. If you are certain docker is running but you are still running into issues running the command ```docker run hello-world``` then google your issue, then search Google and Piazza for your issue. Please understand that this is a large class run by other students who have many commitments outside of this class so *please, please* search thoroughly before making a new post on Piazza. We will try to respond quickly to posts on Piazza but we are only human and have a limited amount of time in each day.


# Docker Usage <a name="usage"></a>

There is a really good tutorial on Docker [here](https://docker-curriculum.com/). For our purposes, we will only need to know the basics of Docker containers and how to run them, but I would highly recommend that tutorial to get a deeper understanding of Docker.

## Containers

A Docker container is an environment in Docker. If you have ever used Virtualenv or Anaconda a docker container is analogous to a Virtualenv environment or an Anaconda environment. The difference being that Virtualenv and Anaconda just create a new set of libraries for each environment whereas docker creates a whole new system totally isolated from the rest of your machine. This means you can do things like run linux programs on Windows, or as in our case make sure that every student in a 200 person class has the exact same set of libraries within an identical working environment. 

## Images

Containers are built from images. You can think of an image like an installer, every time you create a new container from an image you are installing a new environment on your computer based on the specifications of the image. As an example, I created a Docker image for this class, in a bit I will run through how you can download this image and create containers from it. Whenever you run code for this class you should run it within a docker container based on this image. That way everybody will have the same working environment and we wont have strange issue with dependencies. 

## Usage for this class

The image for this class is hosted [here](DOCKER HUB LINK). But one of the nice features of docker is that you can **pull** (download) images from the command line. Let's do download the image for this class from the docker command line. Run 

```
docker pull jamesbartlett/dsd-dev-env
```

After this command finishes you should see something like the following:

```
Using default tag: latest
latest: Pulling from jamesbartlett/dsd-dev-env
d5c6f90da05d: Pull complete 
1300883d87d5: Pull complete 
c220aa3cfc1b: Pull complete 
2e9398f099dc: Pull complete 
dc27a084064f: Pull complete 
e0ce898fb8ab: Pull complete 
30619862a97b: Pull complete 
c04fb5ba4b26: Pull complete 
8f311d32cf2a: Pull complete 
d44e84fc61c0: Pull complete 
2e94bb063d56: Pull complete 
f0ab4fb61de0: Pull complete 
8721fd4b7fbb: Pull complete 
1618bf2e0287: Pull complete 
23be54c5652b: Pull complete 
9931cb1de150: Pull complete 
49b49a1e523a: Pull complete 
e6e255bd2e4f: Pull complete 
Digest: sha256:1702fa1184721f67e4c4394c2074b0f6c294c6545987225933a150963c23400e
Status: Downloaded newer image for jamesbartlett/dsd-dev-env:latest

```

To make sure that it worked run:

```
docker images
```

One of the outputs should be 

```
jamesbartlett/dsd-dev-env                                        latest              26d7c70285c9        8 minutes ago       1.23 GB
```

Now you have the environment installed on your computer. To use the environment we want to create a container from this image. The best way to do that is to use the ```docker run``` command. We want to run jupyter notebooks in our container so we want to open a connection between port 8080 on the container and port 8080 on your computer, to do this we use the ```-p 8080:8080``` option. We also want all of our local files to be available inside the container, so we use the ```-v $(pwd):/root``` option. Finally, we want an interactive terminal to the container we start, so we use the ```-it``` option. The resulting command is:

```
docker run -it -p 8080:8080 -v $(pwd):/root jamesbartlett/dsd-dev-env
```

This will start the container with your files in it and start a jupyter notebook running in the container. We can then access the jupyter notebook at `localhost:8080` or `0.0.0.0:8080`. If you want to access a terminal in the container we can instead run the command:

```
docker run -it -p 8080:8080 -v $(pwd):/root jamesbartlett/dsd-dev-env bash
```

That should be all you need for this class.
