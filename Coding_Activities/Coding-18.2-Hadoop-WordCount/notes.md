# Coding Activity 18.2 Notes
# Executing the Word Count Program in Hadoop

## Activity Overview

In this activity, Hadoop's MapReduce framework was used to process a larger real-world dataset. The dataset selected was the Project Gutenberg text version of *Moby Dick* by Herman Melville.

The objective was to:

- Download a large text file
- Load the file into Hadoop Distributed File System (HDFS)
- Execute a MapReduce Word Count job
- Review the resulting word frequencies
- Understand how Hadoop processes large datasets

This activity demonstrated the complete lifecycle of a Hadoop MapReduce job from ingestion through analysis.

---

# Learning Outcome

✅ Utilize Hadoop to handle Big Data.

---

# Dataset Used

## Source

Project Gutenberg

Book:

```text
Moby Dick
By Herman Melville
```

File Type:

```text
Plain Text UTF-8 (.txt)
```

Approximate Size:

```text
1.2 MB
```

Purpose:

The text file served as the input dataset for the Hadoop Word Count program.

---

# Technologies Used

## Docker

Docker provided the runtime environment for Hadoop.

Benefits:

- Consistent deployment
- Simplified setup
- Container isolation
- Easy system management

---

## Hadoop

Hadoop provides:

```text
Distributed Storage
+
Distributed Processing
```

Core Components:

```text
HDFS
MapReduce
YARN
Hadoop Common
```

---

## HDFS

Hadoop Distributed File System

Purpose:

```text
Distributed Storage Layer
```

Responsible for:

- File storage
- Block management
- Replication
- Fault tolerance

---

## MapReduce

Processing framework used to analyze large datasets.

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

# Step 1: Verify Hadoop Containers

## Command

```bash
docker ps
```

## Result

Verified all Hadoop services were operational.

Containers:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

Status:

```text
healthy
```

### Concept Learned

A Hadoop cluster must be fully operational before HDFS and MapReduce jobs can run.

---

# Step 2: Download Moby Dick

## Download Source

Project Gutenberg:

```text
https://www.gutenberg.org
```

Book:

```text
Moby Dick
```

Downloaded:

```text
Plain Text UTF-8
```

Result:

```text
extracted.txt
```

### Concept Learned

Large text files are commonly used to demonstrate distributed processing workloads.

---

# Step 3: Create a Local Input Folder

## Access NameNode Container

```bash
docker exec -it namenode bash
```

## Create Folder

```bash
mkdir input
```

Verification:

```bash
ls
```

Output:

```text
input
```

### Purpose

The folder stores input data before loading it into HDFS.

### Concept Learned

Files typically enter Hadoop through a staging area before being transferred into HDFS.

---

# Step 4: Copy File to NameNode Container

## Command

```bash
docker cp extracted.txt namenode:/input/
```

Verification:

```bash
ls input
```

Output:

```text
extracted.txt
```

### Purpose

Moves the file from the local operating system into the Hadoop environment.

### Concept Learned

Docker containers have isolated filesystems. Files must be explicitly copied into containers.

---

# Step 5: Create HDFS Input Folder

## Command

```bash
hdfs dfs -mkdir -p /input
```

Verification:

```bash
hdfs dfs -ls /
```

Output:

```text
/input
/rmstate
/user
```

### Purpose

Creates an HDFS location where Hadoop can read the file.

### Concept Learned

MapReduce jobs cannot process files stored only in the container filesystem. Files must reside in HDFS.

---

# Step 6: Copy File into HDFS

## Command

```bash
hdfs dfs -put ./input/* /input
```

Verification:

```bash
hdfs dfs -ls /input
```

Output:

```text
/input/extracted.txt
```

File Size:

```text
1276261 bytes
```

### Concept Learned

HDFS acts as the storage layer for MapReduce processing.

---

# Step 7: Download the Word Count JAR

## Initial Attempt

```bash
curl -L URL
```

Issue:

```text
SSL certificate error
```

---

## Successful Command

```bash
curl -k -L https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar --output hadoop-mapreduce-examples-2.7.1-sources.jar
```

Verification:

```bash
ls
```

Output:

```text
hadoop-mapreduce-examples-2.7.1-sources.jar
```

### Purpose

Downloads the Hadoop Word Count application.

### Concept Learned

Containers occasionally encounter SSL certificate validation issues that require special handling.

---

# Step 8: Execute the Word Count Program

## Command

```bash
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount /input /output
```

---

# What Happened Internally?

## Input Stage

```text
Moby Dick Text File
```

loaded from:

```text
/input/extracted.txt
```

---

## Split Stage

Hadoop split the file into processing units.

```text
Input File
      ↓
Input Split
```

Job Statistics:

```text
Input split bytes = 105
```

---

## Map Phase

The mapper converted each word into:

```text
<word,1>
```

Example:

```text
whale → <whale,1>
ship → <ship,1>
sea → <sea,1>
```

Map Statistics:

```text
Map Tasks = 1
Map Input Records = 22312
Map Output Records = 215845
```

---

## Shuffle and Sort

Hadoop grouped identical words.

Example:

```text
whale {1,1,1,1...}
ship {1,1,1,1...}
```

Statistics:

```text
Reduce Input Groups = 33572
```

---

## Reduce Phase

The reducer aggregated the counts.

Example:

```text
whale 906
ship 794
```

Statistics:

```text
Reduce Output Records = 33572
```

---

## Job Completion

Output:

```text
map 100%
reduce 100%
```

and

```text
Job completed successfully
```

### Concept Learned

MapReduce enables parallel processing and aggregation of large datasets.

---

# Step 9: Review Results

## Command

```bash
hdfs dfs -cat /output/part-r-00000
```

Example Output:

```text
wriggling 3
wrinkled 13
writ 2
write 4
written 3
wrong 2
wrought 6
```

Result:

Hadoop successfully counted every unique word contained in the Moby Dick dataset.

---

# Hadoop Output Files

## List Output Directory

```bash
hdfs dfs -ls /output
```

Expected Files:

```text
_SUCCESS
part-r-00000
```

---

## _SUCCESS

Purpose:

```text
Confirms successful job completion.
```

---

## part-r-00000

Contains:

```text
Final Word Count Results
```

generated by the reducer.

---

# Hadoop Commands Used

## Enter NameNode

```bash
docker exec -it namenode bash
```

---

## Create Local Folder

```bash
mkdir input
```

---

## Create HDFS Folder

```bash
hdfs dfs -mkdir -p /input
```

---

## Upload File to HDFS

```bash
hdfs dfs -put ./input/* /input
```

---

## View HDFS Directory

```bash
hdfs dfs -ls /input
```

---

## Download Word Count JAR

```bash
curl -k -L <url> --output hadoop-mapreduce-examples-2.7.1-sources.jar
```

---

## Execute Word Count

```bash
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount /input /output
```

---

## View Results

```bash
hdfs dfs -cat /output/part-r-00000
```

---

# Understanding MapReduce

## Mapper

Transforms:

```text
Word
```

into:

```text
<Word,1>
```

Example:

```text
whale → <whale,1>
```

---

## Shuffle and Sort

Groups keys:

```text
whale {1,1,1,1}
```

---

## Reducer

Aggregates totals:

```text
whale 906
```

---

# End-to-End Workflow

```text
Download Moby Dick
         ↓
Copy File to Container
         ↓
Create HDFS Folder
         ↓
Upload File to HDFS
         ↓
Download Word Count JAR
         ↓
Run MapReduce Job
         ↓
Map Phase
         ↓
Shuffle & Sort
         ↓
Reduce Phase
         ↓
Store Results in HDFS
         ↓
Display Output
```

---

# Real-World Applications

Word Count demonstrates principles used by:

### Search Engines

Count keyword occurrences.

### Log Analysis

Count user events and system actions.

### Social Media Analytics

Track trending terms.

### Natural Language Processing

Generate vocabulary statistics.

### Utility Analytics

Analyze maintenance records, inspection notes, or operational logs.

### Data Engineering Pipelines

Perform aggregation of large text datasets.

---

# Key Takeaways

1. Hadoop can process large datasets using MapReduce.
2. HDFS stores files before processing occurs.
3. Docker containers provide an easy Hadoop deployment environment.
4. Files must be copied from the container filesystem into HDFS.
5. The mapper converts words into key-value pairs.
6. Shuffle and Sort groups identical keys together.
7. The reducer aggregates word counts.
8. Hadoop generated more than 33,000 unique word groups from the Moby Dick dataset.
9. The Word Count program successfully completed with map and reduce phases reaching 100%.
10. Hadoop demonstrated distributed storage and processing using a real-world text dataset.

---

# Skills Acquired

✅ Hadoop Administration Basics

✅ HDFS File Management

✅ Docker Container Operations

✅ Hadoop MapReduce Execution

✅ Word Count Processing

✅ Distributed Computing Concepts

✅ Big Data Analytics

✅ Data Pipeline Fundamentals

✅ Command Line HDFS Operations

✅ Hadoop Job Monitoring