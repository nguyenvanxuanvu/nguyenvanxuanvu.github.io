---
title:  "Docker"
date: 2026-06-16
permalink: /posts/post-2
tags:
  - docker
---
---

### Table of contents

  - [1. Introduction](#1-introduction)
  - [2. Point out the problems](#2-point-out-the-problems)
  - [3. Main architecture for system](#3-main-architecture-for-system)
  - [4. Some solutions for system to gain the purpose 10k TPS](#4-some-solutions-for-system-to-gain-the-purpose-10k-tps)
  - [5. Complete system](#5-complete-system)
  - [6. Further issues for this system](#6-further-issues-for-this-system)
  - [7. References](#7-references)

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
