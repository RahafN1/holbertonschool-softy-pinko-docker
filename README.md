# holbertonschool-softy-pinko-docker

A Docker project (Novice level) by Derek Webb. The goal is to build the infrastructure for a web application using containers: a **reverse proxy**, a **load balancer**, **two API (back-end) servers**, and **one front-end static-content server**.

## Table of Contents

- [Background](#background)
- [Architecture](#architecture)
- [Requirements](#requirements)
- [Tasks](#tasks)
- [Task 0 - Usage](#task-0---usage)
- [Repository Structure](#repository-structure)
- [Resources](#resources)
- [Author](#author)

## Background

Docker packages an application and everything it needs (libraries, dependencies, configuration) into a portable, isolated **container**. Containers are lightweight, start and stop quickly, and run the same way on a laptop or a server. Multiple containers of the same application can be run side by side to scale it, and managed with Docker Compose or other orchestration tools.

## Architecture

A single server is the entry point for the whole application. It acts as:

1. **Reverse proxy**: routes each request to either the front-end server or the API servers.
2. **Load balancer**: distributes API traffic between the two API servers using **Round Robin**.

```
                         +--> Front-end static-content server
Client --> Reverse Proxy |
          (Load Balancer)|--> API server 1
                         +--> API server 2
```

- **Static content requests** are forwarded to the front-end server. The response goes back through the proxy, so the client never talks to the front-end directly.
- **API requests** go through the Round Robin algorithm, which picks an API server in rotation (1, 2, 1, 2, ...). The response returns through the proxy, so the client never talks to the API servers directly.

## Requirements

- [Docker Desktop](https://www.docker.com/) installed on your **local machine** (not the sandbox)
- Basic familiarity with Docker (images, containers, Dockerfiles)

## Tasks

| # | Task | Directory | Status |
|---|------|-----------|--------|
| 0 | Create Your First Docker Image | `task0` | Done |
| 1 | Back-end | `task1` | Pending |
| 2 | Front-end | `task2` | Pending |
| 3 | Connecting the Front-end and Back-end | `task3` | Pending |
| 4 | Making it Simpler with Docker Compose | `task4` | Pending |
| 5 | Proxy Server | `task5` | Pending |
| 6 | Scale Horizontally | `task6` | Pending |

### Task 0 - Create Your First Docker Image

A `Dockerfile` that:

- is based on the latest Ubuntu image
- runs `apt-get update`
- runs `apt-get upgrade -y`
- prints `Hello, World!` when the container runs

## Task 0 - Usage

Build the image:

```bash
cd task0
docker build -f ./Dockerfile -t softy-pinko:task0 .
```

Run the container:

```bash
docker run -it --rm --name softy-pinko-task0 softy-pinko:task0
```

Expected output:

```
Hello, World!
```

## Repository Structure

```
holbertonschool-softy-pinko-docker/
├── README.md
└── task0/
    └── Dockerfile
```

## Resources

- [Docker Tutorial](https://docs.docker.com/get-started/)
- [Docker Cheatsheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- Proxy vs Reverse Proxy (real-world examples)
- What is a Reverse Proxy? (vs. Forward Proxy)

## Author
Rahaf Alabdalh
