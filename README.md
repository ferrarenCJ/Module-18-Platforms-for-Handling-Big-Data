# Module 18: Platforms for Handling Big Data

**Course:** MIT Professional Education – Data Engineering Program  
**Module:** Module 18 – Platforms for Handling Big Data

---

# Module Overview

Module 18 focused on the technologies, architectures, and tools used to store, manage, and process Big Data. The module introduced Hadoop as one of the most important open-source frameworks for distributed storage and distributed computing.

Students explored Hadoop architecture, the Hadoop ecosystem, Hadoop Distributed File System (HDFS), MapReduce processing, YARN resource management, Docker-based Hadoop deployments, and practical Hadoop data processing using real-world datasets.

The module combined theoretical concepts with hands-on activities, discussions, and a comprehensive final assignment to provide practical experience with Hadoop and Big Data analytics.

---

# Learning Outcomes

Upon completion of this module, students were able to:

✅ Explain the importance of Big Data platforms.

✅ Describe Hadoop architecture and ecosystem components.

✅ Explain distributed storage using HDFS.

✅ Explain distributed processing using MapReduce.

✅ Configure Hadoop using Docker containers.

✅ Load data into HDFS.

✅ Execute Hadoop MapReduce jobs.

✅ Write and execute Java-based Hadoop applications.

✅ Identify real-world Hadoop use cases.

---

# Topics Covered

## Introduction to Big Data

The module began by exploring Big Data and the challenges associated with storing and processing increasingly large datasets.

### Big Data Characteristics

The Five V's of Big Data:

```text
Volume
Velocity
Variety
Veracity
Value
```

Organizations generate data from:

- IoT devices
- Sensors
- Social media
- Business transactions
- Mobile applications
- Websites

---

## Hadoop Fundamentals

Hadoop is an open-source framework designed to process and store large volumes of data using commodity hardware.

### Benefits of Hadoop

```text
Scalability
Fault Tolerance
Distributed Processing
Distributed Storage
Cost Efficiency
```

---

# Hadoop Architecture

Hadoop consists of four primary components:

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

## Hadoop Distributed File System (HDFS)

HDFS is Hadoop's distributed storage layer.

Responsibilities:

- Store data
- Split files into blocks
- Replicate data
- Provide fault tolerance

### NameNode

Responsible for:

```text
Metadata
Block Locations
Directory Structure
```

### DataNode

Responsible for:

```text
Data Storage
Block Replication
Read Operations
Write Operations
```

### Replication Factor

Default replication:

```text
3
```

This ensures data remains available even when nodes fail.

---

## MapReduce

MapReduce is Hadoop's distributed data processing framework.

Processing Workflow:

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

### Map Phase

Transforms input data into:

```text
<Key, Value>
```

pairs.

Example:

```text
whale → <whale,1>
```

---

### Shuffle and Sort

Groups identical keys together.

Example:

```text
whale {1,1,1}
sea {1,1}
```

---

### Reduce Phase

Aggregates values.

Example:

```text
whale 3
sea 2
```

---

## YARN

YARN stands for:

```text
Yet Another Resource Negotiator
```

Purpose:

```text
Resource Management
Job Scheduling
```

### Components

#### Resource Manager

Allocates cluster resources.

#### Node Manager

Manages resources on individual nodes.

#### Application Master

Coordinates execution of submitted applications.

---

## Hadoop Common

Provides shared:

- Libraries
- Utilities
- Scripts
- Configuration Files

required for Hadoop operations.

---

# Hadoop Ecosystem

Beyond its core components, Hadoop provides an extensive ecosystem of supporting tools.

---

## Spark

Provides:

```text
In-Memory Processing
Machine Learning
Streaming Analytics
```

Benefits:

- Faster processing
- Real-time analytics
- Interactive workloads

---

## Hive

Provides:

```text
SQL-like Queries
```

using HiveQL.

Used for:

- Analytics
- Reporting
- Data Warehousing

---

## Pig

Provides:

```text
Pig Latin
```

for data transformation and processing.

---

## HBase

NoSQL database built on Hadoop.

Used for:

```text
Large-Scale Structured Data
```

---

## Mahout

Machine learning framework supporting:

- Classification
- Clustering
- Recommendations

---

## Flume

Used for ingesting:

```text
Unstructured Data
```

Examples:

- Logs
- Event Streams

---

## Sqoop

Used to import and export data between:

```text
Relational Databases
```

and Hadoop.

---

## Oozie

Workflow scheduler used to automate Hadoop jobs.

---

## ZooKeeper

Provides:

```text
Coordination
Synchronization
Configuration Management
```

for Hadoop clusters.

---

## Ambari

Provides:

```text
Cluster Monitoring
Administration
Provisioning
```

for Hadoop environments.

---

# Discussion Activities

---

## Discussion 18.2: Exploring the Hadoop Ecosystem

Research focused on:

- Evolution of Big Data systems
- Hadoop ecosystem components
- Apache Spark benefits
- Industry challenges addressed by Hadoop

Key findings:

- Hadoop supports distributed processing.
- Spark improves performance with in-memory computing.
- Ecosystem tools provide storage, ingestion, analytics, and machine learning capabilities.

---

## Discussion 18.3: Use Cases of Hadoop

Focus area:

```text
Utility Industry
```

Discussion topics:

- Smart meter data
- Sensor data
- Asset monitoring
- Operational analytics

Dataset researched:

```text
U.S. Department of Energy Smart Grid Dataset
```

Benefits of Hadoop:

- Scalable storage
- Parallel processing
- Fault tolerance
- Cost-effective analytics

---

## Self-Study Discussion 18.1

Resources reviewed:

### Guru99 Hadoop Tutorial

```text
https://www.guru99.com/create-your-first-hadoop-program.html
```

### Apache Hadoop Documentation

```text
https://hadoop.apache.org/docs/stable/
```

Key lesson:

Verify HDFS operations frequently using:

```bash
hdfs dfs -ls
hdfs dfs -head
hdfs dfs -tail
```

to simplify troubleshooting.

---

# Coding Activity 18.1

## Setting Up Hadoop in Docker

Objectives:

- Deploy Hadoop containers
- Verify cluster health
- Explore Hadoop services

Containers deployed:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

Skills learned:

- Docker Compose
- Hadoop Service Verification
- Container Management

---

# Coding Activity 18.2

## Executing Word Count in Hadoop

Dataset:

```text
Moby Dick
by Herman Melville
```

Activities completed:

- Upload text file into HDFS
- Download Hadoop examples JAR
- Execute Word Count program
- Review output

Workflow:

```text
Input File
      ↓
Map
      ↓
Shuffle & Sort
      ↓
Reduce
      ↓
Word Counts
```

Skills learned:

- HDFS management
- Hadoop Job Execution
- MapReduce Processing

---

# Final Assignment 18.1

## Platforms for Handling Big Data

Dataset:

```text
SalesData.csv
```

Assignment objectives:

- Store data in HDFS
- Compile Hadoop Java code
- Create a JAR file
- Execute MapReduce
- Aggregate sales by country

---

## Java Components

### SalesCountryDriver.java

Controls job configuration and execution.

---

### SalesMapper.java

Produces:

```text
<Country,1>
```

for each sales record.

---

### SalesCountryReducer.java

Aggregates country totals.

Produces:

```text
<Country,Count>
```

---

## Output Example

```text
Australia      38
Canada         76
France         27
Germany        25
Ireland        49
```

---

# Key Commands Learned

## HDFS

Create directory:

```bash
hdfs dfs -mkdir /inputMapReduce
```

Upload file:

```bash
hdfs dfs -copyFromLocal SalesData.csv /inputMapReduce
```

List files:

```bash
hdfs dfs -ls /inputMapReduce
```

Display file:

```bash
hdfs dfs -cat /inputMapReduce/SalesData.csv
```

---

## MapReduce

Run Hadoop job:

```bash
hadoop jar ProductSalePerCountry.jar \
/inputMapReduce \
/mapreduce_output_sales
```

Display output:

```bash
hdfs dfs -cat /mapreduce_output_sales/part-00000
```

---

# Module 18 Glossary Highlights

Key terms introduced:

- Hadoop
- HDFS
- MapReduce
- YARN
- NameNode
- DataNode
- Application Master
- Resource Manager
- Node Manager
- Cluster
- Replication Factor
- Shuffle Function
- Reduce Task
- Volume
- Velocity
- Variety
- Veracity
- Value

---

# Practical Skills Acquired

✅ Big Data Fundamentals

✅ Hadoop Architecture

✅ HDFS Administration

✅ Docker-Based Hadoop Deployment

✅ YARN Resource Management

✅ Distributed Data Storage

✅ Distributed Data Processing

✅ Java MapReduce Development

✅ Hadoop Job Monitoring

✅ JAR Packaging

✅ Data Aggregation

✅ Big Data Analytics

---

# Real-World Applications

Hadoop is commonly used in:

### Utilities

- Smart meter analytics
- Asset health monitoring
- Predictive maintenance

### Finance

- Fraud detection
- Risk management
- Regulatory compliance

### Healthcare

- Medical analytics
- Patient records processing

### Retail

- Sales analytics
- Recommendation engines

### Telecommunications

- Network monitoring
- Operational analytics

---

# Key Takeaways

1. Hadoop is one of the most important Big Data platforms.
2. HDFS provides scalable distributed storage.
3. MapReduce enables distributed processing across clusters.
4. YARN manages resources and schedules jobs.
5. Docker simplifies Hadoop deployment and testing.
6. Hadoop ecosystems include analytics, machine learning, ingestion, and administration tools.
7. Java applications can be compiled and executed within Hadoop environments.
8. MapReduce efficiently transforms raw data into summarized business insights.
9. Distributed architectures provide scalability and fault tolerance.
10. Hadoop remains a fundamental technology in modern data engineering ecosystems.

---

# Module Completion Summary

| Component | Status |
|------------|------------|
| Videos | ✅ Complete |
| Readings | ✅ Complete |
| Discussion 18.2 | ✅ Complete |
| Discussion 18.3 | ✅ Complete |
| Self-Study Discussion 18.1 | ✅ Complete |
| Coding Activity 18.1 | ✅ Complete |
| Coding Activity 18.2 | ✅ Complete |
| Final Assignment 18.1 | ✅ Complete |
| Module Wrap-Up | ✅ Complete |
| Module Glossary | ✅ Complete |

---

# Conclusion

Module 18 provided a comprehensive introduction to Hadoop and Big Data platforms. Through a combination of conceptual learning and practical implementation, students gained experience working with distributed storage, distributed processing, Hadoop architecture, HDFS administration, MapReduce development, and Docker-based Hadoop deployments. The activities and assignments demonstrated how Hadoop transforms large volumes of raw data into meaningful analytical outcomes, reinforcing essential skills for modern data engineering and analytics roles.