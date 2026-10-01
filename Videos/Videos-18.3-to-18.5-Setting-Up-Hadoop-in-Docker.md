# Videos 18.3 - 18.5: Setting Up Hadoop in a Docker Container

## Overview

These videos demonstrate how to deploy Hadoop using Docker containers. Rather than installing Hadoop directly on an operating system, Docker provides a lightweight and repeatable environment that simplifies Hadoop deployment and testing.

The deployment uses pre-built Hadoop images from the Big Data Europe project.

---

# Why Use Docker for Hadoop?

Installing Hadoop manually can be challenging due to:

- Multiple dependencies
- Configuration complexity
- Java requirements
- Networking configurations

Docker simplifies this process by packaging Hadoop and its dependencies into a reusable image.

Benefits:

- Faster setup
- Consistent environments
- Easy deployment
- Simplified testing
- Reduced configuration effort

---

# Key Docker Concepts

## Docker Image

A Docker image is a template containing:

- Application code
- Dependencies
- Configuration files
- Runtime environment

Images are used to create containers.

### Hadoop Image

This course uses a preconfigured Hadoop image containing:

- Hadoop
- HDFS
- YARN
- Required services

---

## Docker Container

A container is a running instance of a Docker image.

A Hadoop container includes:

- Hadoop processes
- Storage services
- Resource management services

Multiple containers can be deployed from the same image.

---

# Video 18.3: Creating Hadoop Docker Images

## Objective

Download the Hadoop Docker image from the Big Data Europe project.

### General Process

```bash
docker pull bde2020/hadoop-base
```

or the specific image required by the lab instructions.

### Verification

List downloaded images:

```bash
docker images
```

Expected output:

```text
REPOSITORY          TAG
bde2020/*           latest
```

### Key Takeaway

A Docker image serves as the blueprint from which Hadoop containers will be created.

---

# Video 18.4: Creating Hadoop Docker Containers

## Objective

Create and launch a Hadoop container.

### Typical Workflow

Create container:

```bash
docker run
```

Assign:

- Container name
- Ports
- Network settings
- Storage mappings

### Verify Running Containers

```bash
docker ps
```

Example output:

```text
CONTAINER ID
IMAGE
STATUS
PORTS
NAMES
```

### Container Management Commands

Start container:

```bash
docker start <container_name>
```

Stop container:

```bash
docker stop <container_name>
```

Restart container:

```bash
docker restart <container_name>
```

View logs:

```bash
docker logs <container_name>
```

### Key Takeaway

Containers provide isolated environments in which Hadoop services execute.

---

# Video 18.5: Checking Hadoop Status Using a Web Browser

## Objective

Verify that Hadoop services are running correctly.

After startup, Hadoop exposes management interfaces that can be accessed through a web browser.

Typical URLs:

### HDFS Interface

```text
http://localhost:9870
```

### YARN Resource Manager

```text
http://localhost:8088
```

Depending on the Docker image version, ports may vary.

---

# Verifying Hadoop Services

Check that:

✅ NameNode is running

✅ DataNode is running

✅ YARN Resource Manager is running

✅ Cluster health is healthy

✅ No critical service failures exist

---

# Hadoop Components Reviewed

## HDFS (Storage Layer)

Responsibilities:

- Distributed storage
- Block management
- Data replication
- Fault tolerance

---

## NameNode

Responsibilities:

- Maintains metadata
- Tracks file locations
- Coordinates storage operations

### Think Of It As

The master controller of HDFS.

---

## DataNode

Responsibilities:

- Stores data blocks
- Executes storage requests
- Communicates with NameNode

### Think Of It As

The worker servers within HDFS.

---

## YARN

Stands for:

**Yet Another Resource Negotiator**

Responsibilities:

- Resource allocation
- Job scheduling
- Cluster management

---

# Docker and Hadoop Architecture

```text
Docker Image
      ↓
Docker Container
      ↓
Hadoop Services
      ├── HDFS
      │     ├── NameNode
      │     └── DataNode
      │
      └── YARN
            └── Resource Manager
```

---

# Why This Matters

Modern data engineers frequently deploy distributed systems inside containers.

Containerized platforms support:

- Testing
- Development
- Learning environments
- Cloud-native deployments

The same concepts are used in:

- Kubernetes
- Docker Swarm
- AWS ECS
- AWS EKS
- Databricks
- Spark Clusters

---

# Real-World Connection

For a Fleet Intelligence Platform or utility analytics system, Dockerized Hadoop could be used to process:

- Vehicle GPS telemetry
- Fuel transactions
- Smart meter readings
- GIS datasets
- Maintenance history
- IoT sensor streams

using distributed processing techniques.

---

# Key Takeaways

1. Docker images are templates used to deploy containers.
2. Hadoop can be deployed quickly using Docker.
3. Containers isolate Hadoop services and dependencies.
4. HDFS provides distributed storage.
5. NameNode manages filesystem metadata.
6. DataNodes store actual data blocks.
7. YARN manages cluster resources.
8. Web interfaces allow administrators to monitor cluster status.
9. Docker simplifies Hadoop installation and testing.

---

# Exam Notes

## Remember

### Docker

```text
Image → Container
```

### Hadoop

```text
HDFS = Storage
MapReduce = Processing
YARN = Resource Management
```

### Core HDFS Components

```text
NameNode = Metadata Manager
DataNode = Data Storage
```

### Common Browser Interfaces

```text
NameNode UI
http://localhost:9870

YARN UI
http://localhost:8088
```