# Videos

This folder contains notes and summaries for all videos completed during Module 18: Platforms for Handling Big Data. The videos introduced Big Data concepts, Hadoop architecture, HDFS, MapReduce, the Hadoop ecosystem, and practical Hadoop implementation techniques.

---

# Video Summary

| Video | Topic | Status |
|---------|---------|---------|
| Video 18.1 | What Is Big Data? | ✅ Complete |
| Video 18.2 | MapReduce: A Hadoop Framework | ✅ Complete |
| Video 18.3 | Advanced Hadoop Architecture | ✅ Complete |
| Video 18.4 | Executing the Word Count Program | ✅ Complete |
| Video 18.5 | Understanding the Hadoop Ecosystem | ✅ Complete |
| Video 18.6 | Using Hadoop to Handle Big Data | ✅ Complete |
| Video 18.7 | Using Hadoop to Handle Big Data | ✅ Complete |
| Video 18.8 | Using Hadoop to Handle Big Data | ✅ Complete |
| Video 18.9 | Recap: Using Hadoop to Handle Big Data | ✅ Complete |

---

# Video Topics Covered

## Big Data Fundamentals

The module began by introducing the concept of Big Data and why traditional systems struggle to manage modern data volumes.

### The Five V's of Big Data

```text
Volume
Velocity
Variety
Veracity
Value
```

### Common Big Data Sources

- IoT devices
- Sensors
- Smart meters
- Mobile applications
- Websites
- Social media
- Operational systems

---

# Hadoop Fundamentals

The videos introduced Hadoop as an open-source framework for:

```text
Distributed Storage
Distributed Processing
```

of large datasets.

### Benefits of Hadoop

- Scalability
- Fault tolerance
- Parallel processing
- Cost efficiency
- High availability

---

# Hadoop Architecture

Students explored Hadoop's four core components.

## HDFS

### Hadoop Distributed File System

Provides:

```text
Distributed Storage
```

Responsible for:

- File storage
- Block management
- Replication
- Fault tolerance

---

### NameNode

Stores:

```text
Metadata
Directory Structure
Block Locations
```

Acts as the master node.

---

### DataNode

Stores:

```text
Actual Data Blocks
```

Acts as worker nodes.

---

## Replication

Default replication factor:

```text
3
```

Purpose:

- Data protection
- Reliability
- Recovery

---

# MapReduce

MapReduce is Hadoop's distributed processing framework.

---

## Processing Workflow

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

## Mapper

Transforms data into:

```text
<Key, Value>
```

pairs.

Example:

```text
dog → <dog,1>
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

## Reducer

Aggregates grouped values.

Example:

```text
dog 2
cat 1
```

---

# YARN

YARN stands for:

```text
Yet Another Resource Negotiator
```

Purpose:

```text
Resource Management
Job Scheduling
```

---

## YARN Components

### Resource Manager

Allocates resources across the cluster.

---

### Node Manager

Monitors individual nodes and executes workloads.

---

### Application Master

Coordinates execution of individual jobs.

---

# Hadoop Common

Provides:

- Shared Java libraries
- Utilities
- Configuration files
- Core Hadoop services

---

# Hadoop Ecosystem

The module reviewed the broader Hadoop ecosystem and supporting technologies.

---

## Spark

Provides:

```text
In-Memory Processing
Machine Learning
Streaming Analytics
```

Benefits:

- High speed
- Real-time analytics
- Unified analytics platform

---

## Hive

Supports:

```text
SQL-Like Queries
```

through HiveQL.

---

## Pig

Supports:

```text
Data Transformation
```

using Pig Latin.

---

## HBase

Provides:

```text
NoSQL Database
```

functionality.

---

## Mahout

Provides:

```text
Machine Learning
```

capabilities.

---

## Flume

Used to ingest:

```text
Log Data
Streaming Data
```

---

## Sqoop

Transfers data between:

```text
Relational Databases
```

and Hadoop.

---

## Oozie

Schedules Hadoop workflows.

---

## ZooKeeper

Coordinates distributed services.

---

## Ambari

Provides cluster monitoring and administration.

---

# Hadoop in Docker

The videos demonstrated deploying Hadoop within Docker containers.

Benefits:

```text
Fast Setup
Consistency
Portability
Isolation
```

---

## Containers Used

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

---

# Word Count Example

A practical Word Count example was used to illustrate MapReduce operations.

---

## Input

```text
Moby Dick
```

---

## Mapper Output

```text
<word,1>
```

Example:

```text
whale → 1
ship → 1
```

---

## Reducer Output

```text
whale 906
ship 794
```

---

## Learning Outcome

Demonstrated:

- Parallel processing
- Data aggregation
- Distributed computing

---

# Using Hadoop to Handle Big Data

Students learned how Hadoop supports:

```text
Data Ingestion
Storage
Processing
Analytics
Reporting
```

---

## Workflow

```text
Raw Data
    ↓
HDFS
    ↓
MapReduce
    ↓
Analytics
    ↓
Business Insights
```

---

# Practical Skills Developed

Through the videos, students developed an understanding of:

✅ Big Data Concepts

✅ Hadoop Architecture

✅ HDFS

✅ NameNode and DataNode Roles

✅ Data Replication

✅ MapReduce Workflow

✅ YARN Resource Management

✅ Hadoop Ecosystem Tools

✅ Docker-Based Hadoop Deployments

✅ Distributed Processing

---

# Key Commands Introduced

## HDFS

Create directory:

```bash
hdfs dfs -mkdir /input
```

Upload file:

```bash
hdfs dfs -put file.txt /input
```

List files:

```bash
hdfs dfs -ls /input
```

Display file:

```bash
hdfs dfs -cat /input/file.txt
```

---

## Hadoop Jobs

Execute Word Count:

```bash
hadoop jar hadoop-mapreduce-examples.jar \
org.apache.hadoop.examples.WordCount \
/input \
/output
```

---

# Key Video Takeaways

1. Big Data requires distributed platforms for storage and processing.
2. Hadoop provides scalable and fault-tolerant infrastructure.
3. HDFS stores data across distributed nodes.
4. MapReduce processes large datasets in parallel.
5. YARN manages resources and schedules jobs.
6. Hadoop ecosystems include many supporting technologies.
7. Spark extends Hadoop with high-performance analytics.
8. Docker simplifies Hadoop deployment and experimentation.
9. Word Count is a classic example of MapReduce processing.
10. Hadoop remains a foundational technology in modern data engineering.

---

# Folder Structure

```text
Videos/
├── README.md
├── Video-18.1-What-Is-Big-Data.md
├── Video-18.2-MapReduce-A-Hadoop-Framework.md
├── Video-18.3-Advanced-Hadoop-Architecture.md
├── Video-18.4-Executing-the-Word-Count-Program.md
├── Video-18.5-Understanding-the-Hadoop-Ecosystem.md
├── Videos-18.6-to-18.8-Using-Hadoop-to-Handle-Big-Data.md
└── Video-18.9-Recap-Using-Hadoop-to-Handle-Big-Data.md
```

---

# Module 18 Video Completion

✅ All Videos Completed

✅ Video Notes Created

✅ Hadoop Architecture Reviewed

✅ HDFS Concepts Reinforced

✅ MapReduce Workflow Understood

✅ Hadoop Ecosystem Explored

✅ Docker-Based Hadoop Deployment Demonstrated

✅ Word Count Processing Example Completed

✅ Module Recap Completed