# Video 18.2: Overview of Hadoop - A Powerful and Extensible Platform

## Overview

The growth of the internet dramatically increased the amount of data generated worldwide. Organizations began collecting data at scales that traditional database systems could not efficiently handle.

To address these challenges, Apache Hadoop was developed as an open-source framework for distributed storage and distributed processing of large datasets across clusters of commodity hardware.

Hadoop became one of the foundational technologies of the Big Data era and influenced many modern cloud-based data engineering platforms used today.

---

# Why Hadoop Was Created

The web created unprecedented challenges related to:

- Volume of data
- Variety of data
- Velocity of data

Traditional systems faced limitations such as:

- Expensive enterprise hardware
- Single-server bottlenecks
- Limited storage capacity
- Poor scalability

Organizations needed a platform capable of storing and processing massive datasets across many machines.

---

# What Is Hadoop?

Apache Hadoop is an open-source software framework designed for:

- Distributed storage
- Distributed processing
- Large-scale data analytics

Rather than storing and processing data on a single machine, Hadoop distributes work across multiple computers called a cluster.

### Hadoop Benefits

- Horizontal scalability
- Fault tolerance
- Cost efficiency
- Parallel processing
- High availability

---

# Distributed Computing

Distributed computing divides storage and processing tasks among multiple machines.

Instead of:

```text
One Server
 ├─ Store Data
 └─ Process Data
```

Hadoop uses:

```text
Cluster
 ├─ Node 1
 ├─ Node 2
 ├─ Node 3
 ├─ Node 4
 └─ Node N
```

Each node contributes:

- CPU resources
- Memory
- Storage

This allows the cluster to process much larger workloads than a single server.

---

# Commodity Hardware

One key Hadoop innovation was the ability to run on inexpensive, off-the-shelf hardware.

Instead of purchasing:

- High-end enterprise servers
- Specialized storage appliances

Organizations could build clusters using relatively inexpensive machines.

Benefits include:

- Lower costs
- Easier expansion
- Increased flexibility

---

# Core Hadoop Components

## Hadoop Distributed File System (HDFS)

HDFS provides distributed storage.

Responsibilities:

- Store large files
- Split files into blocks
- Replicate data across nodes
- Ensure fault tolerance

Key concept:

> Data is distributed across many machines rather than stored on a single server.

---

## MapReduce

MapReduce provides distributed processing.

Responsibilities:

- Break large processing jobs into smaller tasks.
- Execute tasks in parallel.
- Aggregate results.

Benefits:

- Faster processing
- Better scalability
- Efficient handling of large datasets

---

# Hadoop Cluster Architecture

A Hadoop cluster contains multiple nodes that cooperate to store and process data.

Common architecture includes:

### Master Nodes

Responsible for:

- Cluster coordination
- Metadata management
- Job scheduling

### Worker Nodes

Responsible for:

- Data storage
- Task execution
- Processing workloads

This architecture allows Hadoop to scale from a few machines to thousands of machines.

---

# Fault Tolerance

Hardware failures are expected in large clusters.

Hadoop is designed to continue operating even when individual machines fail.

Methods used include:

- Data replication
- Task reassignment
- Automatic recovery

Benefits:

- Increased reliability
- Higher availability
- Reduced operational risk

---

# Hadoop Ecosystem

Hadoop is more than a single application.

It is a platform that supports many additional tools and services.

Examples include:

- HDFS
- MapReduce
- YARN
- Hive
- Pig
- HBase
- Spark

These tools expand Hadoop's capabilities for analytics, data warehousing, and distributed computing.

---

# Why Hadoop Changed Data Engineering

Before Hadoop:

- Scaling storage was expensive.
- Processing large datasets was difficult.
- Organizations relied on specialized hardware.

After Hadoop:

- Distributed storage became practical.
- Parallel processing became accessible.
- Big Data analytics became more affordable.

Hadoop laid the foundation for many modern cloud services.

Examples:

- Amazon EMR
- AWS Glue
- Databricks
- Apache Spark
- Modern Data Lakes

---

# Enterprise Applications of Hadoop

Organizations use Hadoop for:

### Customer Analytics

- Clickstream analysis
- Recommendation engines
- User behavior analysis

### Predictive Maintenance

- Equipment monitoring
- Failure prediction
- Asset health analytics

### IoT Analytics

- Sensor data analysis
- Fleet telemetry processing
- Smart device monitoring

### Data Warehousing

- Historical data storage
- Enterprise reporting
- Advanced analytics

---

# Connection to SoCalGas

Hadoop concepts are directly relevant to large utility datasets such as:

- SAP maintenance records
- GIS asset data
- Smart meter readings
- Fleet GPS telemetry
- Fuel transaction data
- Leak history datasets

These datasets often exceed the capabilities of traditional processing approaches and benefit from distributed storage and computation.

---

# Key Takeaways

1. Hadoop was created to address Big Data challenges.
2. Hadoop supports distributed storage and distributed processing.
3. Hadoop operates on clusters of commodity hardware.
4. HDFS manages distributed data storage.
5. MapReduce manages distributed data processing.
6. Hadoop is fault tolerant and highly scalable.
7. Hadoop influenced many modern cloud-based data engineering platforms.
8. Understanding Hadoop provides a foundation for understanding large-scale data processing systems.

---

# Exam Notes

### Remember

**Hadoop = Distributed Storage + Distributed Processing**

### Core Components

| Component | Purpose |
|------------|------------|
| HDFS | Distributed Storage |
| MapReduce | Distributed Processing |

### Hadoop Advantages

- Scalability
- Fault Tolerance
- Parallel Processing
- Cost Efficiency

### Key Concept

> Hadoop distributes both data and computation across multiple machines instead of relying on a single server.