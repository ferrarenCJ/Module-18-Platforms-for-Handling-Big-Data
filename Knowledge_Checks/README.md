# Knowledge Checks

This folder contains notes, answers, and key concepts reviewed through the Module 18 Knowledge Checks. These assessments reinforced foundational Hadoop concepts, distributed computing architecture, HDFS storage mechanisms, MapReduce processing, YARN resource management, and the Hadoop ecosystem.

---

# Knowledge Check Summary

| Knowledge Check | Topic | Status |
|-----------------|--------|----------|
| Module 18 Knowledge Checks | Hadoop Fundamentals | ✅ Complete |
| Module 18 Knowledge Checks | HDFS Architecture | ✅ Complete |
| Module 18 Knowledge Checks | MapReduce Framework | ✅ Complete |
| Module 18 Knowledge Checks | YARN Components | ✅ Complete |
| Module 18 Knowledge Checks | Hadoop Ecosystem | ✅ Complete |
| Module 18 Knowledge Checks | Big Data Concepts | ✅ Complete |

---

# Big Data Fundamentals

## Key Concepts Reviewed

### What Is Big Data?

Big Data refers to datasets that are too large, complex, or rapidly generated for traditional systems to effectively process.

Big Data is commonly characterized by the Five V's:

```text
Volume
Velocity
Variety
Veracity
Value
```

---

## The Five V's

### Volume

The amount of data being generated and stored.

Examples:

- Sensor data
- Website logs
- Transaction records
- Video streams

---

### Velocity

The speed at which data is created and processed.

Examples:

- Real-time telemetry
- Financial transactions
- Smart meter readings

---

### Variety

The different formats of data.

Examples:

```text
Structured
Semi-Structured
Unstructured
```

Examples include:

- CSV
- JSON
- XML
- Images
- Videos

---

### Veracity

The quality and accuracy of data.

Ensures:

- Reliability
- Consistency
- Trustworthiness

---

### Value

The business usefulness of data.

Examples:

- Predictive analytics
- Customer insights
- Operational optimization

---

# Hadoop Fundamentals

## What Is Hadoop?

Hadoop is an open-source framework that supports:

```text
Distributed Storage
Distributed Processing
```

for large datasets.

---

## Core Hadoop Components

Hadoop consists of four primary components:

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

# Hadoop Distributed File System (HDFS)

## Purpose

HDFS provides distributed storage across a Hadoop cluster.

Responsibilities:

- Store files
- Replicate data
- Enable fault tolerance
- Support scalability

---

## HDFS Components

### NameNode

Stores:

```text
Metadata
Directory Structure
Block Locations
```

Acts as the:

```text
Master Node
```

---

### DataNode

Stores:

```text
Actual Data Blocks
```

Acts as a:

```text
Worker Node
```

---

## Replication Factor

Default HDFS replication:

```text
3
```

Purpose:

- Fault tolerance
- Data recovery
- High availability

---

## HDFS Workflow

```text
Client
      ↓
NameNode
      ↓
DataNodes
```

---

# MapReduce Framework

## Purpose

MapReduce processes large datasets using distributed computing.

---

## Workflow

```text
Input
 ↓
Map
 ↓
Shuffle & Sort
 ↓
Reduce
 ↓
Output
```

---

## Map Function

Converts input data into:

```text
<Key, Value>
```

pairs.

Example:

```text
dog

→

<dog,1>
```

---

## Shuffle and Sort

Groups identical keys.

Example:

```text
dog {1,1}
cat {1}
```

---

## Reduce Function

Aggregates grouped values.

Example:

```text
dog 2
cat 1
```

---

# MapReduce Components

## Mapper

Responsibilities:

- Read input records
- Create key-value pairs
- Prepare intermediate output

---

## Reducer

Responsibilities:

- Receive grouped keys
- Aggregate values
- Produce final output

---

## Combiner

Responsibilities:

- Perform local aggregation
- Reduce network traffic
- Optimize execution

---

## Partitioner

Responsibilities:

- Determine reducer assignment
- Balance workload
- Improve performance

---

# YARN

## What Does YARN Stand For?

```text
Yet Another Resource Negotiator
```

---

## Purpose

Provides:

```text
Resource Management
Job Scheduling
```

for Hadoop.

---

## YARN Components

### Resource Manager

Responsible for:

- Resource allocation
- Cluster management
- Scheduling

---

### Node Manager

Responsible for:

- Monitoring nodes
- Managing resources
- Running tasks

---

### Application Master

Responsible for:

- Managing individual jobs
- Requesting resources
- Monitoring application execution

---

# Hadoop Common

## Purpose

Provides shared:

- Libraries
- Utilities
- Scripts
- APIs

used by the Hadoop framework.

---

# Hadoop Ecosystem

## Supporting Components

The Hadoop ecosystem extends Hadoop's functionality.

---

### Spark

Provides:

```text
In-Memory Processing
Machine Learning
Streaming Analytics
```

---

### Hive

Provides:

```text
SQL-Like Querying
```

through HiveQL.

---

### Pig

Provides:

```text
Data Transformation
Data Processing
```

using Pig Latin.

---

### HBase

Provides:

```text
NoSQL Database Capabilities
```

---

### Mahout

Provides:

```text
Machine Learning
Classification
Clustering
```

---

### Spark MLlib

Provides:

```text
Machine Learning Algorithms
```

for large-scale analytics.

---

### Flume

Used for:

```text
Unstructured Data Ingestion
```

---

### Sqoop

Used for:

```text
Database Imports and Exports
```

---

### Oozie

Provides:

```text
Workflow Scheduling
```

---

### ZooKeeper

Provides:

```text
Cluster Coordination
```

---

### Ambari

Provides:

```text
Cluster Monitoring
Administration
```

---

# Docker and Hadoop

## Purpose

Docker simplifies Hadoop setup and management.

Benefits:

- Fast deployment
- Environment consistency
- Isolation
- Portability

---

## Common Docker Commands

### Start Environment

```bash
docker compose up -d
```

---

### View Containers

```bash
docker ps
```

---

### Access NameNode

```bash
docker exec -it namenode bash
```

---

### Copy Files

```bash
docker cp file.txt namenode:/home
```

---

# HDFS Commands Reviewed

Create directory:

```bash
hdfs dfs -mkdir /input
```

---

Upload file:

```bash
hdfs dfs -put file.txt /input
```

---

List files:

```bash
hdfs dfs -ls /
```

---

Display file:

```bash
hdfs dfs -cat /input/file.txt
```

---

View beginning of file:

```bash
hdfs dfs -head /input/file.txt
```

---

View end of file:

```bash
hdfs dfs -tail /input/file.txt
```

---

# Practical Concepts Reinforced

Throughout the knowledge checks, students reinforced understanding of:

✅ Big Data Concepts

✅ Hadoop Architecture

✅ HDFS Components

✅ NameNode and DataNode Functions

✅ Replication and Fault Tolerance

✅ MapReduce Workflow

✅ Mapper and Reducer Roles

✅ YARN Architecture

✅ Resource Management

✅ Hadoop Ecosystem Tools

✅ Docker-Based Hadoop Deployment

---

# Most Important Exam Topics

## Hadoop Core Components

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

## HDFS Components

```text
NameNode
DataNode
```

---

## MapReduce Steps

```text
Map
Shuffle
Sort
Reduce
```

---

## YARN Components

```text
Resource Manager
Node Manager
Application Master
```

---

## Five V's of Big Data

```text
Volume
Velocity
Variety
Veracity
Value
```

---

# Quick Review Questions

## What stores actual data blocks?

Answer:

```text
DataNode
```

---

## What stores metadata?

Answer:

```text
NameNode
```

---

## What does YARN manage?

Answer:

```text
Resources and Job Scheduling
```

---

## What does the Mapper produce?

Answer:

```text
<Key, Value> Pairs
```

---

## What does the Reducer do?

Answer:

```text
Aggregates Values
```

---

## What is the default HDFS replication factor?

Answer:

```text
3
```

---

## What does HDFS stand for?

Answer:

```text
Hadoop Distributed File System
```

---

## What does YARN stand for?

Answer:

```text
Yet Another Resource Negotiator
```

---

# Key Takeaways

1. Hadoop provides distributed storage and processing.
2. HDFS stores data across multiple nodes.
3. Replication improves reliability and fault tolerance.
4. MapReduce provides scalable distributed computation.
5. YARN handles resource allocation and scheduling.
6. Hadoop ecosystems extend functionality beyond core Hadoop components.
7. Docker simplifies Hadoop deployment.
8. Large datasets can be processed in parallel across clusters.
9. Hadoop remains a foundational big data technology.
10. Understanding Hadoop architecture is essential for modern data engineering.

---

# Module 18 Knowledge Checks Completion

✅ Big Data Concepts Reviewed

✅ Hadoop Fundamentals Mastered

✅ HDFS Architecture Understood

✅ MapReduce Workflow Reinforced

✅ YARN Components Reviewed

✅ Hadoop Ecosystem Components Studied

✅ Docker and Hadoop Concepts Applied

✅ Module 18 Knowledge Checks Completed