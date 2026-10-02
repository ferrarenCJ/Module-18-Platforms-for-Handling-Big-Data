# Module 18: Glossary

## Application Master

Within the YARN framework, the Application Master works on a single job submitted to the framework. Each Application Master coordinates an application's execution in the cluster and manages faults. It negotiates resources from the Resource Manager and works with the Node Manager to execute and monitor component tasks.

---

## Big Data

Big Data refers to extremely large datasets that can be analyzed computationally to reveal patterns, trends, and associations, particularly related to human behavior and interactions.

---

## Blocks (Chunks)

Blocks, also known as chunks, are fragments of data or code that are divided into smaller pieces for storage and processing.

---

## Cluster

A cluster is a group of computers working together on the same task. The computers within a cluster can be viewed as a single system.

---

## Combine Function (Combiner)

Within the MapReduce framework, the Combine Function reduces the mapper output into a more simplified form before it is transferred to reducers.

---

## Hadoop Common (Common Utilities)

Hadoop Common includes the Java libraries, Java files, utilities, and scripts required for all Hadoop components to function together.

---

## DataNode

DataNodes are responsible for storing data within a Hadoop cluster. Increasing the number of DataNodes increases storage capacity. DataNodes store the actual data blocks managed by HDFS.

---

## Default Replication Factor

In HDFS, the default replication factor determines how many copies of each data block are stored across the cluster for fault tolerance. The default replication factor is:

```text
3
```

---

## Hadoop

Hadoop is an open-source framework used for distributed storage and distributed processing of large datasets.

The four main Hadoop components are:

- HDFS
- MapReduce
- YARN
- Hadoop Common

---

## Hadoop Distributed File System (HDFS)

HDFS is Hadoop's distributed storage system. It stores large datasets by dividing them into blocks and distributing those blocks across DataNodes in a cluster.

Key features:

- Distributed storage
- Fault tolerance
- Scalability
- Replication

---

## Hadoop Ecosystem

The Hadoop Ecosystem consists of Hadoop's primary components and supporting tools used for storage, processing, resource management, analytics, machine learning, data ingestion, and administration.

Core components include:

- HDFS
- MapReduce
- YARN
- Hadoop Common

---

## HistoryServer

HistoryServer is one of Hadoop's service containers used to store and display historical information about completed MapReduce jobs.

---

## JAR File

A JAR (Java Archive) file is a package that contains compiled Java classes and associated resources used to deploy Java applications.

Example:

```text
ProductSalePerCountry.jar
```

---

## Job Scheduler

The Job Scheduler is part of the YARN framework. It divides large jobs into smaller tasks and distributes those tasks across cluster nodes to maximize processing efficiency.

---

## Map Function

Within MapReduce, the Map Function processes input data and converts it into key-value pairs.

Example:

```text
Input:
Canada

Output:
<Canada,1>
```

---

## Mapping

The mapping phase takes smaller subsets of input data and performs computations on each subset independently.

---

## Map Task

A Map Task is a processing unit within the MapReduce framework that converts input records into key-value pairs.

---

## MapReduce

MapReduce is Hadoop's distributed processing framework used to process large datasets across multiple servers in parallel.

Workflow:

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

## Master Node

In Hadoop, a Master Node manages and coordinates operations performed by DataNodes and other worker nodes.

Examples:

- NameNode
- Resource Manager

---

## NameNode

The NameNode is the master component of HDFS responsible for maintaining metadata about stored data.

Examples:

- File locations
- Directory structure
- Block information

---

## Node Manager

Within YARN, the Node Manager monitors individual nodes and manages user jobs and resource usage on those nodes.

---

## Partition Function (Partitioner)

The Partition Function determines how mapper output key-value pairs are distributed to reducers.

The partitioning process helps ensure balanced workload distribution across reducers.

---

## Reduce Task (Reducer)

The Reduce Task receives grouped key-value pairs from the Shuffle and Sort phase and aggregates the values.

Example:

```text
Input:
Canada {1,1,1}

Output:
Canada 3
```

The reducer executes after mapping is complete.

---

## Resource Manager

Within YARN, the Resource Manager is responsible for managing cluster resources and allocating them to applications.

Responsibilities include:

- Resource allocation
- Scheduling
- Cluster-wide management

---

## Shuffle Function

The Shuffle Function groups mapper outputs by key and prepares them for reducer processing.

Example:

```text
Mapper Output

Canada 1
Canada 1
Germany 1
```

After Shuffle:

```text
Canada {1,1}
Germany {1}
```

---

## Slave Node

A Slave Node refers to a DataNode that stores data and performs work assigned by the NameNode.

---

## Splitting Stage

The Splitting Stage divides an input dataset into smaller subsets before processing begins.

Example:

```text
Large File
      ↓
Multiple Input Splits
```

---

## Value

Value is one of the Big V's of Big Data.

Data only becomes useful when organizations discover how to use it to generate business value and actionable insights.

---

## Variety

Variety is one of the Big V's of Big Data.

It refers to the many formats in which data can arrive:

- Structured
- Semi-structured
- Unstructured

Examples:

- Tables
- JSON
- XML
- Images
- Video
- Sensor Data

---

## Velocity

Velocity is one of the Big V's of Big Data.

It refers to the speed at which data is generated, transmitted, and processed.

Examples:

- IoT sensors
- Smart devices
- Streaming applications
- Financial transactions

---

## Veracity

Veracity is one of the Big V's of Big Data.

It refers to the accuracy, quality, reliability, and trustworthiness of data.

Organizations must ensure data quality to avoid biased or inaccurate results.

---

## Volume

Volume is one of the Big V's of Big Data.

It refers to the massive amount of data generated and stored by organizations.

Examples:

- Terabytes
- Petabytes
- Exabytes

Sources include:

- Websites
- Mobile applications
- Sensors
- Security cameras
- Business systems

---

## Yet Another Resource Negotiator (YARN)

YARN stands for:

```text
Yet Another Resource Negotiator
```

YARN is Hadoop's resource management and job scheduling framework.

Responsibilities:

- Resource allocation
- Job scheduling
- Workload management
- Cluster coordination

Major components include:

- Resource Manager
- Node Manager
- Application Master

---

# Module 18 Key Terms Summary

## Hadoop Storage

- HDFS
- NameNode
- DataNode
- Blocks
- Replication Factor

---

## Hadoop Processing

- MapReduce
- Map Function
- Reduce Task
- Shuffle Function
- Partition Function
- Combine Function

---

## Hadoop Resource Management

- YARN
- Resource Manager
- Node Manager
- Application Master

---

## Big Data Concepts

- Volume
- Velocity
- Variety
- Veracity
- Value

---

## Cluster Concepts

- Cluster
- Master Node
- Slave Node
- Splitting Stage

---

## Supporting Components

- Hadoop Common
- HistoryServer
- JAR File
- Job Scheduler