# Mini-Lesson 18.2: MapReduce - A Hadoop Framework

## Overview

MapReduce is one of the core processing frameworks within Hadoop. It allows organizations to process extremely large datasets by dividing the work across multiple machines operating in parallel.

Instead of processing an entire dataset on a single server, MapReduce breaks the data into smaller chunks, distributes the work across a cluster, and combines the results into a final output.

This distributed processing model enables Hadoop to efficiently handle Big Data workloads.

---

# What Is MapReduce?

MapReduce is a programming model and processing framework used by Hadoop for distributed data processing.

Its primary purpose is to:

- Split large datasets into smaller chunks
- Process the chunks simultaneously
- Aggregate the results into a final dataset

### Example

Suppose:

- Dataset size = 5 TB
- Cluster size = 10,000 servers
- Each server processes 256 MB

Instead of one machine processing the entire dataset, Hadoop distributes portions of the data across thousands of servers, significantly reducing processing time through parallel execution.

---

# Why MapReduce Is Important

Traditional processing:

```text
Large Dataset
      ↓
 Single Server
      ↓
    Output
```

MapReduce processing:

```text
Large Dataset
      ↓
 Divide into Chunks
      ↓
 Multiple Servers Process Data
      ↓
 Combine Results
      ↓
 Final Output
```

Benefits:

- Faster processing
- Better scalability
- Fault tolerance
- Efficient use of cluster resources

---

# MapReduce Workflow

The MapReduce pipeline consists of four primary stages:

```text
Input Data
     ↓
    Map
     ↓
 Combine (Optional)
     ↓
 Partition
     ↓
   Reduce
     ↓
 Final Output
```

---

# Step 1: Map Function

The Map phase reads input records and transforms them into key-value pairs.

Input:

```text
Student A
Student B
Student C
```

Output:

```text
<Student A, 1>
<Student B, 1>
<Student C, 1>
```

### Responsibilities

- Read data
- Transform records
- Create key-value pairs
- Process data in parallel

### Key Concept

Each mapper works independently on a portion of the dataset.

---

# Map Task Processing

Suppose there are 500 records.

Hadoop may create:

```text
Mapper 1
Mapper 2
Mapper 3
...
Mapper N
```

Each mapper processes a subset of the records simultaneously.

The number of mappers depends on:

- Dataset size
- Block size
- Available memory
- Cluster resources

---

# Step 2: Combine Function (Optional)

A Combiner performs partial aggregation before data is sent across the cluster.

Purpose:

- Reduce network traffic
- Minimize data movement
- Improve performance

Example:

Mapper Output:

```text
<Student B,1>
<Student B,1>
```

Combiner Output:

```text
<Student B,2>
```

### Benefits

- Less data transferred
- Faster execution
- Reduced cluster workload

### Important Note

The Combiner stage is optional.

---

# Step 3: Partition Function

The Partitioner organizes and routes key-value pairs to reducers.

Responsibilities:

- Group similar keys together
- Determine reducer assignments
- Prepare data for final aggregation

Example:

```text
<Student A>{1,1}
<Student B>{1,2,1}
<Student C>{1,1,1}
```

The partitioner ensures all identical keys are sent to the same reducer.

---

# Step 4: Reduce Function

The Reduce phase receives grouped values and performs final aggregation.

Input:

```text
<Student A>{1,1}
<Student B>{1,2,1}
<Student C>{1,1,1}
```

Output:

```text
<Student A>{2}
<Student B>{4}
<Student C>{3}
```

Responsibilities:

- Aggregate results
- Perform calculations
- Generate final output

---

# Complete MapReduce Example

## Mapper Output

```text
Mapper1
<Student A,1>
<Student B,1>
<Student C,1>

Mapper2
<Student B,1>
<Student B,1>
<Student C,1>

Mapper3
<Student A,1>
<Student C,1>
<Student B,1>
```

---

## Combiner Output

```text
Combiner1
<Student A,1>
<Student B,1>
<Student C,1>

Combiner2
<Student B,2>
<Student C,1>

Combiner3
<Student A,1>
<Student B,1>
<Student C,1>
```

---

## Partitioner Output

```text
<Student A>{1,1}
<Student B>{1,2,1}
<Student C>{1,1,1}
```

---

## Reducer Output

```text
<Student A>{2}
<Student B>{4}
<Student C>{3}
```

---

# Word Count Example

One of the most common MapReduce examples is Word Count.

Input:

```text
hello world
hello hadoop
```

Mapper Output:

```text
<hello,1>
<world,1>
<hello,1>
<hadoop,1>
```

Reducer Output:

```text
<hello,2>
<world,1>
<hadoop,1>
```

This is the same exercise that will be implemented later in Module 18.

---

# Advantages of MapReduce

## Parallel Processing

Multiple servers process data simultaneously.

## Scalability

Can scale from a few nodes to thousands of nodes.

## Fault Tolerance

If one node fails, Hadoop can rerun the task on another node.

## Cost Efficiency

Runs on commodity hardware rather than specialized systems.

## Performance

Processes large datasets much faster than traditional single-server approaches.

---

# Real-World Applications

MapReduce can be used for:

### Search Engines

- Indexing web pages
- Ranking search results

### Recommendation Systems

- Product recommendations
- Video recommendations

### Log Analytics

- Clickstream analysis
- Application monitoring

### Utility Data Processing

- Smart meter analytics
- Asset monitoring
- Fleet telemetry analysis

### Machine Learning

- Feature engineering
- Large-scale data preprocessing

---

# Relationship Between HDFS and MapReduce

Hadoop consists of two major components:

| Component | Purpose |
|------------|------------|
| HDFS | Distributed Storage |
| MapReduce | Distributed Processing |

### Simple Analogy

```text
HDFS Stores Data
MapReduce Processes Data
```

Together they form the core of the Hadoop ecosystem.

---

# Exam Notes

## Remember the Pipeline

```text
Map
 ↓
Combine (Optional)
 ↓
Partition
 ↓
Reduce
```

## Mapper

Produces:

```text
<Key, Value>
```

pairs.

## Combiner

- Optional
- Performs local aggregation

## Partitioner

- Groups keys
- Sends data to reducers

## Reducer

- Generates final output

---

# Key Takeaways

1. MapReduce is Hadoop's distributed processing framework.
2. Large datasets are divided into smaller chunks.
3. Mappers create key-value pairs.
4. Combiners optionally perform local aggregation.
5. Partitioners organize data before reduction.
6. Reducers aggregate results into final outputs.
7. MapReduce enables massive parallel processing.
8. Word Count is the most common MapReduce example.
9. HDFS stores data, while MapReduce processes data.
10. Together, HDFS and MapReduce make Hadoop a powerful Big Data platform.