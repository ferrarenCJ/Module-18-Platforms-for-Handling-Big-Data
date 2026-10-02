# Videos 18.6 - 18.8: Using Hadoop to Handle Big Data

## Overview

These videos demonstrate how Hadoop can be used to process large datasets using the MapReduce framework. Specifically, the activity focuses on implementing a Word Count program, one of the most common examples used to learn Hadoop and MapReduce.

The process consists of:

1. Creating input data
2. Loading data into Hadoop
3. Setting up the Word Count application
4. Executing the MapReduce job
5. Reviewing the output results

This exercise demonstrates how Hadoop distributes processing across a cluster and aggregates the results using the MapReduce framework.

---

# Learning Objectives

By completing these videos, students will be able to:

- Create input data for Hadoop processing
- Access a Hadoop container
- Execute a MapReduce job
- Understand Word Count processing
- Review output stored in HDFS
- Observe Hadoop's distributed processing workflow

---

# Video 18.6: Creating Input for a Hadoop Container

## Objective

Create an input file that will be used by Hadoop to calculate word frequency.

---

## What Is Word Count?

Word Count is a classic Hadoop example that counts how many times each word appears in a text file.

Example Input:

```text
hadoop is powerful

hadoop is scalable

big data uses hadoop
```

Desired Output:

```text
hadoop 3
is 2
powerful 1
scalable 1
big 1
data 1
uses 1
```

---

## Create Input File

Example:

```bash
nano input.txt
```

or

```bash
echo "hadoop is powerful" > input.txt
```

The input file contains text data that Hadoop will process.

---

## Purpose of Input Data

The input file serves as:

```text
Raw Data
```

for the MapReduce job.

The file will later be copied into HDFS for processing.

---

## Concepts Learned

### Input Dataset

The source data used by Hadoop.

### HDFS Input Directory

Location where Hadoop stores incoming files before processing.

### Data Preparation

Data must exist before a MapReduce task can execute.

---

# Video 18.7: Setting Up a Hadoop Container to Run a Word Count Program

## Objective

Prepare the Hadoop environment and access the Hadoop container where the MapReduce program will be executed.

---

# Access the Hadoop Container

Example Command:

```bash
docker exec -it namenode bash
```

Purpose:

- Enter Hadoop environment
- Execute HDFS commands
- Run Hadoop jobs

---

# Verify HDFS

Example:

```bash
hdfs dfs -ls /
```

Purpose:

Verify that the Hadoop filesystem is operational.

---

# Create Directories

Example:

```bash
hdfs dfs -mkdir /input
```

Purpose:

Create a location for input files.

---

# Upload Input File

Example:

```bash
hdfs dfs -put input.txt /input
```

Purpose:

Copy the local file into HDFS.

---

# Verify Upload

Example:

```bash
hdfs dfs -ls /input
```

Output:

```text
/input/input.txt
```

This confirms the file was successfully uploaded to HDFS.

---

# Word Count Program

Hadoop includes sample MapReduce applications.

Typical location:

```text
share/hadoop/mapreduce/
```

Common example JAR:

```text
hadoop-mapreduce-examples
```

This JAR contains sample jobs including Word Count.

---

# Concepts Learned

### HDFS Commands

Used to manage files stored within Hadoop.

### Hadoop Container Access

Provides administrative access to Hadoop services.

### File Upload Process

Data must be transferred into HDFS before processing can occur.

---

# Video 18.8: Executing the Word Count Program and Inspecting Results

## Objective

Execute the Hadoop Word Count application and view the generated results.

---

# Execute Word Count

Example Command:

```bash
hadoop jar \
/opt/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-examples.jar \
wordcount \
/input \
/output
```

---

# What Happens Internally?

## Step 1: Input Split

The input file is divided into blocks.

```text
Input File
     ↓
Input Splits
```

---

## Step 2: Map Phase

Each word is transformed into key-value pairs.

Example:

Input:

```text
hadoop hadoop data
```

Mapper Output:

```text
<hadoop,1>
<hadoop,1>
<data,1>
```

---

## Step 3: Shuffle and Sort

Hadoop groups values with matching keys.

Output:

```text
<hadoop>{1,1}
<data>{1}
```

---

## Step 4: Reduce Phase

Values are aggregated.

Output:

```text
<hadoop,2>
<data,1>
```

---

# Verify Output Directory

Command:

```bash
hdfs dfs -ls /output
```

Typical Result:

```text
part-r-00000
_SUCCESS
```

### Meaning

```text
_SUCCESS
```

indicates the job completed successfully.

---

# View Results

Command:

```bash
hdfs dfs -cat /output/part-r-00000
```

Example Output:

```text
big 1
data 1
hadoop 3
is 2
powerful 1
scalable 1
uses 1
```

---

# Understanding MapReduce Through Word Count

The Word Count program demonstrates the entire Hadoop workflow.

```text
Input File
      ↓
Map
      ↓
<Key, Value>
      ↓
Shuffle & Sort
      ↓
Reduce
      ↓
Output File
```

---

# Why Word Count Is Important

Word Count demonstrates:

- Distributed processing
- Key-value pair creation
- Aggregation
- Parallel execution
- HDFS data flow

Many enterprise Hadoop jobs follow the same pattern.

---

# Real-World Applications

Word Count concepts are applied to:

### Search Engines

Count keywords across billions of pages.

### Log Analysis

Count events and user actions.

### Social Media Analytics

Track keyword popularity.

### Utility Analytics

Count incidents, work orders, inspections, or asset events.

### Machine Learning

Generate features from large text datasets.

---

# Hadoop Command Summary

## Enter Hadoop Container

```bash
docker exec -it namenode bash
```

---

## Create HDFS Directory

```bash
hdfs dfs -mkdir /input
```

---

## Upload File

```bash
hdfs dfs -put input.txt /input
```

---

## List Directory

```bash
hdfs dfs -ls /input
```

---

## Run Word Count

```bash
hadoop jar \
hadoop-mapreduce-examples.jar \
wordcount \
/input \
/output
```

---

## View Output Directory

```bash
hdfs dfs -ls /output
```

---

## Display Results

```bash
hdfs dfs -cat /output/part-r-00000
```

---

# Exam Notes

## Word Count Steps

```text
Input
 ↓
Map
 ↓
Shuffle and Sort
 ↓
Reduce
 ↓
Output
```

---

## Mapper Output

Produces:

```text
<Key, Value>
```

pairs.

Example:

```text
<word,1>
```

---

## Reducer Output

Aggregates totals.

Example:

```text
<hadoop,3>
```

---

## HDFS Output Files

```text
_SUCCESS
part-r-00000
```

---

# Key Takeaways

1. Hadoop can process large datasets using MapReduce.
2. Word Count is a classic Hadoop example application.
3. Input data must be uploaded to HDFS before processing.
4. Hadoop jobs are typically executed from within a Hadoop container.
5. Map tasks create key-value pairs for each word.
6. Reducers aggregate matching keys into final totals.
7. Results are stored back into HDFS.
8. The `_SUCCESS` file indicates successful job completion.
9. Word Count demonstrates the complete MapReduce processing pipeline.
10. The same Hadoop workflow can be applied to many real-world Big Data problems.