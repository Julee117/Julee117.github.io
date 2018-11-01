---
layout: post
title:      "What is Docker?"
date:       2018-11-01 16:05:14 +0000
permalink:  what_is_docker
---


Docker is an open source software to develop, deploy and run applications using containers. Docker containers are lightweight and are easily scalable. They can also be deployed anywhere such as on physical and virtual machines as well as the cloud.

A container is a running instance of an image. An image is a read-only template that includes what is needed to run an application such as code, libraries, environment variables and configuration files. Dockerfile is used to run the image, which is a text file with a list of steps to perform to create that image. 

The difference between virtual machines and Docker containers is that virtual machines run on top of a hypervisor. The hypervisor emulates a computer’s hardware so every virtual machine has to include a full operating system. Docker containers share the kernel of the host operating system that they run on which makes them smaller in size because we don’t need to run an entire operating system.

![](https://www.aquasec.com/wiki/download/attachments/2854029/docker-birthday-3-intro-to-docker-slides-18-638.jpg?version=1&modificationDate=1515522843003&api=v2)

There are several reasons to use Docker. One is that it provides a consistent environment for your application from development to production. With Docker, your application runs the same despite which server or whose machine it is running on so this allows less time to be spent setting up environments and debugging environment-specific issues. You can also rapidly run a new process on a server because the image is preconfigured and installed. Each Docker container is isolated from other containers and has its own resources. This ensures a clean removal from your application when you no longer need it and delete it. 

You can get started with Docker [here](https://docs.docker.com/).
