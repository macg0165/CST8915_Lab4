# Lab 4 - Introduction to Docker
**Name:** Angus MacGillivary<br>
**Course:** CST8915<br>
**Section:** 11 <br> 
**Lab:** 4<br>
**Date:** October 13, 2026<br>

## Video Demo
[Link](https://youtu.be/feSqvzT-vWk?si=BX4-rx09miYdyaeL)

## Reflection Questions
### i. What are the main differences between a Docker image and a Docker container?

Docker Images and Docker Containers are both core components to the Docker workflow, with distinct yet complementary purposes.  Docker Images are the read-only template files built from Dockerfiles which act as a reference for containers as they are built..  Containers are effectively Linux processes, isolated using namespaces and cgroups, that re built using Images.
### ii. Explain how Docker's layered architecture improves efficiency.
Docker Images don't store dependencies themselves, they refer to shared **layers** containing the individual filesystem changes in the Dockerfile. Newer Docker Images may then use older cached layers instead of building the image from scratch every time.  This provides two main benefits to the Docker host:  reduced build time on containers and reduced disk from images.
### iii. Why does each container get its own writable layer?
Upon creation, each Container gains an extra layer on top of the read-only layers from the Image: a read-write layer.  This allows Containers to share image layers while still being able to modify their own virtual file systems, as all of the changes are stored in the writable layer that only they have access to.
### iiii. What are the benefits of using Docker Compose over running containers individually?
Docker Compose provides a shared interface across multiple containers.  This allows configurations such as network, volumes and environment variables to be written in a single YAML file, simplifying the development process.