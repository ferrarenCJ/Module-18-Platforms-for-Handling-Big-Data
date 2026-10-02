# Coding Activity 18.1 Notes
# Setting Up Hadoop in a Docker Container

## Activity Overview

In this activity, Hadoop was deployed using Docker containers provided by the Big Data Europe Project. The objective was to create a fully functioning Hadoop environment, verify that all services were healthy, and confirm that the Hadoop Distributed File System (HDFS) web interface was accessible.

The environment was deployed using Docker Compose, which allowed multiple Hadoop services to be launched with a single command.

---

# Learning Outcome

✅ Set up Hadoop in a Docker container.

---

# Technologies Used

## Docker

Docker is a containerization platform that packages applications and their dependencies into isolated environments called containers.

Benefits:

- Fast deployment
- Environment consistency
- Simplified installation
- Easy scalability

---

## Docker Compose

Docker Compose orchestrates multiple containers using a YAML configuration file.

Primary file:

```text
docker-compose.yml
```

Purpose:

- Deploy multi-container applications
- Configure networking
- Configure storage volumes
- Simplify service management

---

## Hadoop

Hadoop is an open-source framework used for:

- Distributed storage
- Distributed processing
- Big Data analytics

Core Hadoop Components:

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

# Environment Information

## Docker Version

Command:

```bash
docker --version
```

Result:

```text
Docker version 29.8.1
```

---

# Step 1: Review Existing Docker Containers

## Command

```bash
docker ps
```

## Purpose

Displays all currently running containers.

## Result

No Hadoop containers were running prior to deployment.

Output displayed:

```text
CONTAINER ID
IMAGE
COMMAND
CREATED
STATUS
PORTS
NAMES
```

### Screenshot

```text
step1-docker-ps.png
```

### Concept Learned

Containers must be running before services become available to users.

---

# Step 2: Clone the Hadoop Repository

## Repository

```text
https://github.com/big-data-europe/docker-hadoop
```

## Command

```bash
git clone git@github.com:big-data-europe/docker-hadoop.git
```

## Result

The Hadoop Docker repository was successfully cloned locally.

Output:

```text
Cloning into 'docker-hadoop'
Receiving objects...
Resolving deltas...
```

### Screenshot

```text
step2-git-clone.png
```

### Concept Learned

Infrastructure-as-Code allows developers and engineers to recreate environments consistently using version-controlled configuration files.

---

# Step 3: Locate docker-compose.yml

## Commands

```bash
cd docker-hadoop
```

```bash
dir
```

## Files Found

```text
docker-compose.yml
docker-compose-v3.yml
```

## Purpose

The docker-compose file contains all service definitions required to deploy the Hadoop cluster.

### Screenshot

```text
step3-docker-compose-file.png
```

### Concept Learned

Docker Compose uses YAML files to define application architecture and deployment requirements.

---

# Step 4: Deploy Hadoop Containers

## Command

```bash
docker compose up -d
```

## Parameter

```text
-d
```

Stands for:

```text
Detached Mode
```

The containers run in the background.

---

# Hadoop Services Created

The deployment successfully created:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

Docker automatically:

- Created the network
- Created persistent volumes
- Downloaded required images
- Started Hadoop services

### Screenshot

```text
step4-docker-compose-up.png
```

---

# Container Purpose

## NameNode

Role:

```text
HDFS Master Node
```

Responsibilities:

- Metadata management
- File tracking
- Block tracking
- Filesystem coordination

---

## DataNode

Role:

```text
HDFS Worker Node
```

Responsibilities:

- Store file blocks
- Process read requests
- Process write requests

---

## ResourceManager

Role:

```text
YARN Master Service
```

Responsibilities:

- Resource allocation
- Job scheduling
- Cluster management

---

## NodeManager

Role:

```text
YARN Worker Service
```

Responsibilities:

- Execute tasks
- Monitor node resources
- Communicate with ResourceManager

---

## HistoryServer

Role:

```text
MapReduce History Tracking
```

Responsibilities:

- Store completed job information
- Job auditing
- Performance review

---

# Step 5: Verify Container Health

## Command

```bash
docker ps
```

## Result

All Hadoop services reported:

```text
(healthy)
```

Containers Verified:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

Example Output:

```text
Up 9 minutes (healthy)
```

### Screenshot

```text
step5-healthy-containers.png
```

### Why This Matters

Healthy status confirms:

- Service startup completed
- Internal health checks passed
- Hadoop services are operational

---

# Step 6: Verify Hadoop Web Interface

## URL

```text
http://localhost:9870
```

## Result

Successfully opened the Hadoop NameNode interface.

Displayed:

```text
Overview
Cluster Summary
Live Nodes
Storage Capacity
HDFS Statistics
```

Observed Status:

```text
namenode:9000 (active)
```

### Screenshot

```text
step6-hdfs-web-ui.png
```

---

# HDFS Observations

The NameNode dashboard displayed:

```text
Live Nodes: 1
Dead Nodes: 0
```

This confirms:

- DataNode connectivity
- HDFS operation
- Successful cluster communication

---

# Important Hadoop Concepts Reinforced

## HDFS

Stands for:

```text
Hadoop Distributed File System
```

Purpose:

```text
Distributed Storage
```

---

## NameNode

Stores:

```text
Metadata
```

Examples:

- File names
- File locations
- Block locations

---

## DataNode

Stores:

```text
Actual File Blocks
```

---

## Block Storage

Default HDFS Block Size:

```text
128 MB
```

Example:

```text
500 MB File
```

becomes:

```text
128 MB
128 MB
128 MB
116 MB
```

---

## Replication

Default Replication Factor:

```text
3
```

Purpose:

```text
Fault Tolerance
```

Each block is stored three times across the cluster.

---

## YARN

Stands for:

```text
Yet Another Resource Negotiator
```

Responsibilities:

```text
Job Scheduling
Resource Management
```

---

# Docker Networking

Docker automatically created a network for Hadoop services.

Purpose:

```text
Allow container-to-container communication
```

Examples:

```text
namenode ↔ datanode
resourcemanager ↔ nodemanager
```

---

# Ports Used

## NameNode Web Interface

```text
9870
```

Access URL:

```text
http://localhost:9870
```

---

## NameNode Service

```text