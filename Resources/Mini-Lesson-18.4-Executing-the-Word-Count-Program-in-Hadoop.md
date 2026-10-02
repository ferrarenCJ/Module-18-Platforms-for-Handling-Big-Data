# Mini-Lesson 18.4: Executing the Word Count Program in Hadoop

## Overview

The Word Count program is one of the most common examples used to demonstrate how Hadoop's MapReduce framework works.

The objective of the program is simple:

```text
Count the number of occurrences of each word in one or more text files.
```

Although simple, the Word Count example illustrates the complete Hadoop processing pipeline:

```text
Input Files
     ↓
HDFS Storage
     ↓
Map Phase
     ↓
Shuffle and Sort
     ↓
Reduce Phase
     ↓
Output Results
```

This lesson also introduces fundamental HDFS operations such as creating directories, copying files, listing files, and viewing output.

---

# Learning Objectives

By completing this lesson, students should be able to:

- Create input files for Hadoop processing
- Upload files into HDFS
- Execute a Hadoop MapReduce job
- Run a Word Count program
- Inspect MapReduce output
- Use common HDFS commands
- Understand the complete MapReduce workflow

---

# MapReduce Word Count Example

## Input Text

File 1:

```text
it was the best of times
it was the worst of times
```

File 2:

```text
it was the age of wisdom
it was the age of foolishness
```

---

## Mapper Output

The mapper converts text into key-value pairs.

Example:

```text
it        1
was       1
the       1
best      1
of        1
times     1
```

Repeated for every word encountered.

---

## Shuffle and Sort

Hadoop groups identical keys together.

Example:

```text
it      {1,1,1,1}
was     {1,1,1,1}
the     {1,1,1,1}
```

---

## Reducer Output

The reducer aggregates the values.

Example:

```text
it      4
was     4
the     4
```

---

# Prerequisites

Before running Word Count, verify:

✅ Docker installed

✅ Hadoop Docker containers running

✅ NameNode healthy

✅ DataNode healthy

✅ HDFS operational

Check status:

```bash
docker ps
```

Expected:

```text
namenode
datanode
nodemanager
resourcemanager
historyserver
```

All should show:

```text
healthy
```

---

# Step 1: Access the NameNode Container

Open a command shell inside the NameNode container.

Example:

```bash
docker exec -it namenode bash
```

Purpose:

- Access Hadoop commands
- Manage HDFS
- Run MapReduce jobs

---

# Step 2: Create an Input Directory

Create a local directory inside the container:

```bash
mkdir input
```

Verify:

```bash
ls
```

Output:

```text
input
```

---

# Step 3: Create Input Files

Create the first text file:

```bash
echo "it was the best of times it was the worst of times" > ./input/f1.txt
```

Create the second text file:

```bash
echo "it was the age of wisdom it was the age of foolishness" > ./input/f2.txt
```

---

# Step 4: Verify Input Files

List files:

```bash
ls ./input
```

Expected output:

```text
f1.txt
f2.txt
```

This confirms the files were successfully created.

---

# Step 5: Create an HDFS Directory

Hadoop cannot process files stored only in the local container filesystem.

Create an HDFS directory:

```bash
hadoop fs -mkdir -p input
```

Purpose:

```text
Create a folder in HDFS
```

---

# Step 6: Copy Local Files to HDFS

Upload the text files:

```bash
hdfs dfs -put ./input/* input
```

Purpose:

```text
Container Filesystem
        ↓
       HDFS
```

This allows Hadoop to access the files.

---

# Step 7: Verify Files in HDFS

List HDFS contents:

```bash
hdfs dfs -ls input
```

Expected output:

```text
input/f1.txt
input/f2.txt
```

Verification confirms the files were successfully copied into HDFS.

---

# Step 8: Download the Word Count Program

Download the Hadoop MapReduce examples JAR file:

```bash
curl -L \
https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar \
--output hadoop-mapreduce-examples-2.7.1-sources.jar
```

Purpose:

```text
Obtain the Hadoop WordCount application
```

---

# Step 9: Verify JAR Download

List files:

```bash
ls
```

Expected output:

```text
hadoop-mapreduce-examples-2.7.1-sources.jar
```

The JAR file should now exist in the NameNode container.

---

# Step 10: Execute the Word Count Program

Run:

```bash
hadoop jar \
hadoop-mapreduce-examples-2.7.1-sources.jar \
org.apache.hadoop.examples.WordCount \
input \
output
```

---

# What Happens Internally?

## Input Stage

```text
f1.txt
f2.txt
```

Data enters Hadoop.

---

## Split Stage

Files are divided into blocks.

```text
Input Files
      ↓
Input Splits
```

---

## Map Phase

Words become key-value pairs.

Example:

```text
<it,1>
<was,1>
<the,1>
```

---

## Shuffle & Sort

Matching words are grouped.

Example:

```text
it {1,1,1,1}
was {1,1,1,1}
```

---

## Reduce Phase

Counts are aggregated.

Example:

```text
it      4
was     4
the     4
```

---

## Output

Results written into HDFS.

```text
output/
```

---

# Step 11: View Output Results

Display results:

```bash
hdfs dfs -cat output/part-r-00000
```

Example output:

```text
age             2
best            1
foolishness     1
it              4
of              4
the             4
times           2
was             4
wisdom          1
worst           1
```

---

# Output Files

List the contents of the output directory:

```bash
hdfs dfs -ls output
```

Typical output:

```text
_SUCCESS
part-r-00000
```

---

## _SUCCESS

Meaning:

```text
MapReduce Job Completed Successfully
```

---

## part-r-00000

Contains:

```text
Word Counts
```

generated by the reducer.

---

# Common HDFS Commands

## Create Folder

```bash
hadoop fs -mkdir -p input
```

---

## Upload Files

```bash
hdfs dfs -put ./input/* input
```

---

## List Folder Contents

```bash
hdfs dfs -ls output
```

---

## Display File Contents

```bash
hdfs dfs -cat output/part-r-00000
```

---

## Delete Folder

```bash
hdfs dfs -rm -r hdfs://namenode:9000/user/root/output_folder_name
```

---

# End-to-End Workflow

```text
Create Text Files
          ↓
Create HDFS Input Folder
          ↓
Upload Files to HDFS
          ↓
Download WordCount JAR
          ↓
Run Hadoop Job
          ↓
Map Phase
          ↓
Shuffle & Sort
          ↓
Reduce Phase
          ↓
Output Directory
          ↓
View Results
```

---

# Why Word Count Matters

Word Count demonstrates several important Hadoop concepts:

### HDFS Operations

- File uploads
- File storage
- Output retrieval

### MapReduce Processing

- Mapping
- Sorting
- Reducing

### Distributed Computing

- Parallel execution
- Data partitioning
- Aggregate computation

---

# Real-World Applications

The same pattern used by Word Count can be applied to:

- Search engine indexing
- Website analytics
- Log analysis
- Social media trend detection
- Customer behavior analysis
- IoT event processing
- Utility asset analytics

---

# Exam Notes

## Word Count Pipeline

```text
Input
 ↓
Split
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

Produces:

```text
<Key, Value>
```

Example:

```text
<word,1>
```

---

## Reducer

Aggregates values.

Example:

```text
<hadoop,5>
```

---

## Result File

```text
part-r-00000
```

---

## Success Indicator

```text
_SUCCESS
```

---

# Key Takeaways

1. Word Count is the classic Hadoop MapReduce example.
2. Files must be stored in HDFS before Hadoop can process them.
3. HDFS commands are used to manage distributed files.
4. The mapper creates key-value pairs for each word.
5. Shuffle and Sort groups matching keys together.
6. The reducer aggregates totals for each word.
7. Results are written back to HDFS.
8. The `_SUCCESS` file indicates successful completion.
9. `part-r-00000` contains the final output data.
10. Word Count illustrates the complete Hadoop MapReduce workflow.