---
title:  "Docker"
date: 2026-06-16
permalink: /posts/post-2
tags:
  - docker
---
---

## 1. Definition
    - Container: Completely isolated environments, they can have their own processes or services, their own network interfaces, their own mounts, just like VM, except all share the same OS kernel.
    - OCI: Open Container Initiative
    - Image: like a VM template -> 1 - many container (Dockerfile build -> Image -> Push Docker Hub)
    - Docker Engine: Free, open source

## 2. Command
    - docker run
    - docker ps (only running) -> docker ps -a 
    - docker stop id/name
    - docker rm silly_sammet
    - docker images
    - docker rmi 
    - docker pull
    - Run command inside container: docker exec id ....
    - docker run -d (image): mean like not see the log
    - docker attach container_id: re-attached to container output
    - docker system prune (remove all stopped containers, ...)
