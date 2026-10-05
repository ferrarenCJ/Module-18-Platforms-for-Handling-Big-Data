# Coding Activities

This folder contains the hands-on exercises completed during Module 18: Platforms for Handling Big Data. These activities provided practical experience with Hadoop, HDFS, Docker, and MapReduce.

---

# Activity Summary

| Activity | Topic | Status |
|-----------|-----------|-----------|
| Coding Activity 18.1 | Setting Up Hadoop in Docker | ✅ Complete |
| Coding Activity 18.2 | Executing the Word Count Program in Hadoop | ✅ Complete |

---

# Coding Activity 18.1: Setting Up Hadoop in Docker

## Overview

This activity introduced the deployment and configuration of a Hadoop environment using Docker containers. The objective was to create a functional Hadoop cluster that could be used throughout the module for HDFS operations and MapReduce processing.

---

## Learning Objectives

- Understand Hadoop deployment architecture.
- Learn how to deploy Hadoop using Docker.
- Verify Hadoop services and containers.
- Access Hadoop administrative interfaces.

---

## Technologies Used

- Docker Desktop
- Docker Compose
- Hadoop
- HDFS
- YARN

---

## Hadoop Services Deployed

The Hadoop environment consisted of the following containers:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

---

## Key Commands

### Start Hadoop Environment

```bash
docker compose up -d
```

### Verify Running Containers

```bash
docker ps
```

### Access NameNode Container

```bash
docker exec -it namenode bash
```

---

## Verification

The Hadoop environment was validated by:

- Verifying all containers were running.
- Confirming healthy container status.
- Accessing Hadoop management interfaces.
- Confirming NameNode availability.

---

## Skills Acquired

✅ Docker Container Management

✅ Hadoop Deployment

✅ Hadoop Service Verification

✅ Cluster Administration Basics

✅ Container Monitoring

---

# Coding Activity 18.2: Executing the Word Count Program in Hadoop

## Overview

This activity demonstrated how Hadoop MapReduce processes large datasets using the classic Word Count example. A text version of *Moby Dick* was uploaded to HDFS and processed using Hadoop's distributed computing framework.

---

## Learning Objectives

- Load data into HDFS.
- Execute Hadoop MapReduce jobs.
- Analyze MapReduce output.
- Understand distributed processing concepts.

---

## Dataset

### Source

Project Gutenberg

Book:

```text
Moby Dick
By Herman Melville
```

File:

```text
extracted.txt
```

Approximate Size:

```text
1.2 MB
```

---

## Workflow

```text
Download Dataset
        ↓
Copy Data into Container
        ↓
Create HDFS Folder
        ↓
Upload File to HDFS
        ↓
Execute Word Count Program
        ↓
Map Phase
        ↓
Shuffle & Sort
        ↓
Reduce Phase
        ↓
Review Output
```

---

## HDFS Commands

### Create Input Directory

```bash
hdfs dfs -mkdir -p /input
```

### Upload File

```bash
hdfs dfs -put ./input/* /input
```

### Verify Upload

```bash
hdfs dfs -ls /input
```

---

## Download Hadoop Example JAR

```bash
curl -k -L https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar \
--output hadoop-mapreduce-examples-2.7.1-sources.jar
```

---

## Execute Word Count

```bash
hadoop jar \
hadoop-mapreduce-examples-2.7.1-sources.jar \
org.apache.hadoop.examples.WordCount \
/input \
/output
```

---

## MapReduce Processing

### Map Phase

Transforms text into:

```text
<word,1>
```

Example:

```text
whale → <whale,1>
ship → <ship,1>
```

---

### Shuffle & Sort

Groups identical words.

Example:

```text
whale {1,1,1}
ship {1,1}
```

---

### Reduce Phase

Aggregates counts.

Example:

```text
whale 906
ship 794
```

---

## Output Review

### Display Results

```bash
hdfs dfs -cat /output/part-r-00000
```

Example:

```text
written 11
write 4
wrong 2
wrought 6
```

---

## Job Statistics

Example metrics collected during processing:

```text
Map Input Records = 22312
Map Output Records = 215845
Reduce Output Records = 33572
```

These statistics demonstrate Hadoop's ability to process large datasets efficiently using distributed computation.

---

## Skills Acquired

✅ HDFS Administration

✅ Hadoop File Management

✅ MapReduce Processing

✅ Word Count Analysis

✅ Distributed Computing

✅ Big Data Analytics

---

# Concepts Reinforced

Throughout these activities, the following Hadoop concepts were reinforced:

## HDFS

- Distributed storage
- Data replication
- Fault tolerance
- Block management

---

## MapReduce

- Mapping
- Shuffle and Sort
- Reducing
- Aggregation

---

## YARN

- Resource allocation
- Job scheduling
- Application management

---

## Docker

- Container deployment
- Service orchestration
- Environment management

---

# Key Takeaways

1. Docker simplifies Hadoop deployment and testing.
2. HDFS stores large datasets across distributed nodes.
3. Hadoop uses replication to improve reliability.
4. MapReduce enables parallel processing of large datasets.
5. The Word Count application demonstrates fundamental MapReduce concepts.
6. Hadoop can efficiently process large text datasets.
7. HDFS and MapReduce work together to provide storage and analytics capabilities.
8. Distributed processing improves scalability and performance.
9. Hadoop jobs can be monitored and validated through generated statistics.
10. Practical experience with Hadoop administration and processing is essential for data engineering roles.

---

# Folder Structure

```text
Coding_Activities/
├── Coding-18.1-Setting-Up-Hadoop-in-Docker/
│   ├── README.md
│   └── notes.md
│
└── Coding-18.2-Executing-WordCount-in-Hadoop/
    ├── README.md
    └── notes.md
```

---

# Module 18 Coding Activities Completion

✅ Coding Activity 18.1 Completed

✅ Coding Activity 18.2 Completed

✅ Hadoop Environment Successfully Deployed

✅ HDFS Operations Successfully Performed

✅ MapReduce Word Count Successfully Executed

✅ Big Data Processing Concepts Applied