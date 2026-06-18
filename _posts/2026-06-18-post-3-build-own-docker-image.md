---
title:  "Build Custom Base Image & Push to Hub"
date: 2026-06-16
permalink: /posts/post-3
tags:
  - docker
  - custom
---
---

# Example: Build Custom Golang Base Image & Push to Docker Hub

## Step 1: Create Dockerfile with golang:1.21-alpine + Extra Packages

**File: `Dockerfile.golang`**

```dockerfile
FROM golang:1.21-alpine

LABEL maintainer="your-email@example.com"

# Install additional packages
RUN apk add --no-cache \
    ca-certificates \
    git \
    curl \
    wget \
    make \
    gcc \
    musl-dev \
    tzdata \
    bash \
    postgresql-client \
    mysql-client \
    redis

# Set Go environment variables
ENV GOPATH=/go \
    GOROOT=/usr/local/go \
    PATH=$GOPATH/bin:/usr/local/go/bin:$PATH

WORKDIR /workspace

# Verify installations
RUN go version && \
    git --version && \
    curl --version

CMD ["bash"]
```

---

## Step 2: Build the Custom Image Locally

```bash
docker build -f Dockerfile.golang -t my-golang-base:1.21 .
```

**Test it locally:**
```bash
docker run -it my-golang-base:1.21
# Inside container, verify:
go version
git --version
curl --version
```

---

## Step 3: Login to Docker Hub

```bash
docker login
# Enter your Docker Hub username and password
```

---

## Step 4: Tag Image for Docker Hub

Replace `YOUR-DOCKER-USERNAME` with your actual Docker Hub username:

```bash
docker tag my-golang-base:1.21 YOUR-DOCKER-USERNAME/golang-base:1.21
docker tag my-golang-base:1.21 YOUR-DOCKER-USERNAME/golang-base:latest
```

**Example:**
```bash
docker tag my-golang-base:1.21 xuanvu/golang-base:1.21
docker tag my-golang-base:1.21 xuanvu/golang-base:latest
```

---

## Step 5: Push to Docker Hub

```bash
docker push YOUR-DOCKER-USERNAME/golang-base:1.21
docker push YOUR-DOCKER-USERNAME/golang-base:latest
```

---

## Step 6: Use Your Custom Base Image

Now you can use it in other projects:

```dockerfile
FROM YOUR-DOCKER-USERNAME/golang-base:1.21

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -o main .

EXPOSE 8080
CMD ["./main"]
```

---

## Useful Alpine Packages to Add

| Package | Purpose |
|---------|---------|
| `git` | Version control |
| `curl` | HTTP requests |
| `wget` | File downloads |
| `make` | Build automation |
| `gcc` | C compiler (needed for some Go packages) |
| `postgresql-client` | PostgreSQL CLI |
| `mysql-client` | MySQL CLI |
| `redis` | Redis CLI |
| `bash` | Shell scripting |
| `ca-certificates` | SSL/TLS certificates |

---

## Quick Reference Commands

```bash
# Build
docker build -f Dockerfile.golang -t YOUR-DOCKER-USERNAME/golang-base:1.21 .

# Push
docker push YOUR-DOCKER-USERNAME/golang-base:1.21

# Pull (use in other projects)
docker pull YOUR-DOCKER-USERNAME/golang-base:1.21
```

---

## Verify on Docker Hub

1. Go to https://hub.docker.com/r/YOUR-DOCKER-USERNAME/golang-base
2. Your image should be visible
3. Others can now pull it: `docker pull YOUR-DOCKER-USERNAME/golang-base:1.21`
