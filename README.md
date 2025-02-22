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

A Virtual Machine has a complete OS on it. It's the hardware that is virtualized.  


@5/59
---
EOF
