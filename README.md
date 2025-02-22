# Docker course by Travis 

https://www.youtube.com/watch?v=i7ABlHngi1Q

- We will dockerize a React app
- We'll also dockerize a Wordpress website

# High-level Overview

## Docker image & containers

Simply put, Docker is container management software.  
A Docker image is a blueprint that contains the instructions for building a container.  

An image is made up of layers, such as:
- a base layer (Alpine Linux in many cases)
- your software files 
- dependencies 
- config files, environment variables
- ...

A container is a ready-to-roll application built from a docker image.  
A container is also a running instance of a docker image.  

## Why do we use containers?

- ease of use: easy to build and run, easy to stop or get rid of, easy to store and share
- flexibility: you can build your containers with whatever you want, it's easy to add, remove or replace the layers
- self-sufficiency: no need to worry about compatibility, it works the same on any host system since it contains everything needed to run 

## VM vs Container

A Virtual Machine has its own OS. It's the hardware that is virtualized.  
VMs use the hardware resources of the host system thanks to what we call a "**hypervisor**".  

Containers don't have an actual OS, they use a virtualized OS provided by a container engine such as Docker.  

VMs take up more space and more resources from the host system. They also take longer to boot up.  
Containers can boot up instantly, since there's no OS to boot.  

Despite all the obvious advantages containers offer, VMs are still relevant in some use cases.  

# Let's practice Docker

## Setup

- Download and install Docker Desktop
- 


@7/59
---
EOF
