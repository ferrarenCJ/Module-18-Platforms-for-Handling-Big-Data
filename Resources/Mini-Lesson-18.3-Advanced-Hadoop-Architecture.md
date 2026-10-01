# Mini-Lesson 18.3: Advanced Hadoop Architecture

## Overview

Hadoop is an open-source framework written in Java that enables organizations to store and process massive datasets across clusters of commodity hardware.

Major organizations that have utilized Hadoop include:

- Facebook
- Yahoo
- Netflix
- eBay

Hadoop architecture consists of four main components:

1. HDFS (Hadoop Distributed File System)
2. MapReduce
3. YARN (Yet Another Resource Negotiator)
4. Hadoop Common (Common Utilities)

In this lesson, the focus is on HDFS, YARN, and Hadoop Common.

---

# Hadoop Architecture

```text
                Hadoop
                    |
    -----------------------------------
    |          |           |          |
   HDFS    MapReduce     YARN     Hadoop Common
 Storage   Processing   Resources   Utilities
```

---

# Hadoop Distributed File System (HDFS)

## What is HDFS?

The Hadoop Distributed File System (HDFS) is Hadoop's storage layer.

HDFS is designed to:

- Store huge datasets
- Operate on commodity hardware
- Support fault tolerance
- Scale across clusters

Unlike traditional file systems, HDFS is optimized for large files rather than many small files.

---

# HDFS Components

HDFS contains two primary node types:

## NameNode

The NameNode is the master node of HDFS.

Responsibilities:

- Stores metadata
- Tracks file locations
- Manages filesystem structure
- Directs DataNodes

### Think Of It As

The directory manager of the entire Hadoop cluster.

### Stores

- File names
- File locations
- Block locations
- Transaction logs

The NameNode does **not** store actual data.

---

## DataNode

The DataNode is the worker node of HDFS.

Responsibilities:

- Stores actual data blocks
- Handles read requests
- Handles write requests
- Reports status to NameNode

### Key Concept

The more DataNodes a cluster contains, the more storage capacity is available.

---

# HDFS Block Storage

Files stored in HDFS are divided into blocks.

### Default Block Size

```text
128 MB
```

---

## Example

A file uploaded to HDFS:

```text
500 MB
```

Will be divided into:

```text
Block 1 = 128 MB
Block 2 = 128 MB
Block 3 = 128 MB
Block 4 = 116 MB
```

The blocks are distributed across DataNodes.

---

# HDFS Replication

Because Hadoop often runs on inexpensive hardware, failures are expected.

To prevent data loss, HDFS automatically creates copies of blocks.

### Default Replication Factor

```text
3
```

Meaning:

```text
Original Block
Copy 1
Copy 2
```

are stored on different DataNodes.

---

# Example

```text
Block A

DataNode 1
DataNode 3
DataNode 7
```

If one node fails, the data remains available.

### Benefits

- Fault tolerance
- High availability
- Data durability

---

# HDFS Summary

| Component | Purpose |
|------------|------------|
| NameNode | Stores metadata |
| DataNode | Stores actual data |
| Block | Unit of storage (128 MB) |
| Replication | Creates backup copies |

---

# YARN (Yet Another Resource Negotiator)

## What Is YARN?

YARN is Hadoop's resource management and job scheduling framework.

Main functions:

1. Resource Management
2. Job Scheduling

---

# Job Scheduling

Large jobs are divided into smaller tasks and distributed across cluster nodes.

Example:

```text
Large Job
      ↓
Small Tasks
      ↓
Distributed Across Nodes
```

The scheduler determines:

- Task priorities
- Task dependencies
- Execution timing
- Resource requirements

---

# Resource Management

YARN manages cluster resources such as:

- CPU
- Memory
- Storage
- Containers

Its goal is to maximize resource utilization across the cluster.

---

# YARN Architecture

```text
                Resource Manager
                        |
      ---------------------------------------
      |                 |                  |
 Node Manager     Node Manager      Node Manager
      |                 |                  |
 Containers       Containers       Containers
```

---

# Resource Manager

The Resource Manager is the master component of YARN.

Responsibilities:

- Allocate resources
- Manage cluster resources
- Schedule workloads
- Coordinate processing

### Think Of It As

The traffic controller for Hadoop jobs.

---

# Node Manager

Each node contains a Node Manager.

Responsibilities:

- Monitor local resources
- Manage containers
- Execute tasks
- Communicate with Resource Manager

### Think Of It As

The operations manager for a single machine.

---

# Application Master

The Application Master manages a single running application.

Responsibilities:

- Request resources
- Coordinate execution
- Monitor tasks
- Handle failures

### Key Concept

One Application Master is created per application.

---

# Container

A container is a collection of computing resources allocated to a task.

Resources may include:

- CPU cores
- RAM
- Disk space

A container provides a controlled environment where an application can execute.

### Example

```text
Container
├── 2 CPU Cores
├── 4 GB RAM
└── Storage Allocation
```

---

# YARN Summary

| Component | Responsibility |
|------------|------------|
| Resource Manager | Cluster-wide resource allocation |
| Node Manager | Node-level monitoring |
| Application Master | Application execution |
| Container | Assigned computing resources |

---

# Hadoop Common

## What Is Hadoop Common?

Hadoop Common contains the libraries, utilities, scripts, and APIs required by all Hadoop components.

It acts as the foundation of the Hadoop ecosystem.

---

# Responsibilities of Hadoop Common

Provides:

- Java libraries
- Utility scripts
- Configuration files
- Shared APIs

Used by:

- HDFS
- MapReduce
- YARN

Without Hadoop Common, the other Hadoop components could not communicate effectively.

---

# Why Hadoop Common Is Important

Hadoop Common enables:

### Storage Operations

Supports HDFS data storage and retrieval.

### Processing Operations

Supports MapReduce execution.

### Resource Coordination

Allows MapReduce and YARN to communicate.

### Cluster Management

Provides common functionality shared across the platform.

---

# Complete Hadoop Architecture

```text
                    Hadoop
                        |
    ------------------------------------------------
    |                 |              |             |
   HDFS          MapReduce         YARN      Hadoop Common
   Storage       Processing      Resources      Utilities
    |
    |
 -----------------
 |               |
NameNode     DataNodes
```

---

# Real-World Example

Suppose Netflix uploads terabytes of streaming logs.

### HDFS

Stores the logs across many DataNodes.

### YARN

Allocates resources required to analyze the logs.

### MapReduce

Processes the logs in parallel.

### Hadoop Common

Provides the shared services and libraries that allow all components to work together.

---

# Exam Notes

## Four Core Hadoop Components

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

## NameNode

```text
Master Node
Stores Metadata
```

---

## DataNode

```text
Worker Node
Stores Data
```

---

## Default HDFS Block Size

```text
128 MB
```

---

## Default Replication Factor

```text
3
```

---

## YARN

Stands for:

```text
Yet Another Resource Negotiator
```

Functions:

- Job Scheduling
- Resource Management

---

# Key Takeaways

1. Hadoop consists of HDFS, MapReduce, YARN, and Hadoop Common.
2. HDFS provides distributed storage.
3. NameNodes manage metadata.
4. DataNodes store actual file blocks.
5. Files are divided into 128 MB blocks.
6. HDFS uses a default replication factor of 3.
7. YARN handles job scheduling and resource management.
8. Resource Managers allocate cluster resources.
9. Node Managers manage individual cluster nodes.
10. Hadoop Common provides the libraries and utilities required for all Hadoop services.