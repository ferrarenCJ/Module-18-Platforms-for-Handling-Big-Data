# Final Assignment 18.1 Notes
# Platforms for Handling Big Data

## Assignment Overview

This assignment demonstrated how Hadoop can be used to store, process, and analyze large datasets using the Hadoop Distributed File System (HDFS) and the MapReduce programming framework.

The assignment was divided into two parts:

### Part 1

Ingesting data into Hadoop storage using HDFS.

### Part 2

Performing a MapReduce operation to aggregate sales transactions by country using Java MapReduce programs.

The dataset used in this assignment was:

```text
SalesData.csv
```

which contained sales transaction information organized by country.

---

# Learning Outcome

✅ Write a Java program to access the Hadoop database.

✅ Use MapReduce to process large datasets.

✅ Utilize HDFS for distributed storage.

✅ Compile and execute Hadoop Java applications.

---

# Technologies Used

## Docker

Containerized Hadoop environment.

Benefits:

- Simple deployment
- Consistent configuration
- Portable environment

---

## Hadoop

Open-source Big Data processing platform.

Provides:

```text
Distributed Storage
Distributed Processing
```

---

## HDFS

Hadoop Distributed File System

Purpose:

```text
Store Large Datasets
```

Features:

- Data replication
- Fault tolerance
- Horizontal scaling
- Distributed storage

---

## MapReduce

Distributed computation framework.

Purpose:

```text
Process Data Across Multiple Nodes
```

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

## Java

Used to develop Hadoop applications.

Files used:

```text
SalesCountryDriver.java
SalesMapper.java
SalesCountryReducer.java
```

---

# Dataset

## File

```text
SalesData.csv
```

Purpose:

Contains sales records used to calculate transaction totals by country.

---

# Part 1: Ingesting Data into HDFS

---

# Step 1: Extract testprogram.zip

The assignment package contained:

```text
Manifest.txt
SalesCountryDriver.java
SalesCountryReducer.java
SalesMapper.java
SalesData.csv
```

Purpose:

Provide all files necessary to execute the Hadoop MapReduce application.

---

# Step 2: Copy Files into the NameNode

## Command

```bash
docker cp testprogram namenode:/home
```

---

## Verification

```bash
cd /home

ls
```

Output:

```text
testprogram
```

Contents:

```text
Manifest.txt
SalesCountryDriver.java
SalesCountryReducer.java
SalesMapper.java
SalesData.csv
```

---

## Concept Learned

Docker containers maintain isolated filesystems.

Files must be copied into the Hadoop environment before they can be processed.

---

# Step 3: Create HDFS Folder

## Command

```bash
hdfs dfs -mkdir /inputMapReduce
```

Purpose:

Create an HDFS location to store input data.

---

# Upload Sales Data

## Command

```bash
hdfs dfs -copyFromLocal SalesData.csv /inputMapReduce
```

Verification:

```bash
hdfs dfs -ls /inputMapReduce
```

Output:

```text
SalesData.csv
```

---

## Concept Learned

MapReduce jobs can only process files stored in HDFS.

---

# Step 4: Verify the Dataset

## Commands

Review beginning of file:

```bash
hdfs dfs -head /inputMapReduce/SalesData.csv
```

Review end of file:

```bash
hdfs dfs -tail /inputMapReduce/SalesData.csv
```

Review complete file:

```bash
hdfs dfs -cat /inputMapReduce/SalesData.csv
```

---

## Result

Verified that:

```text
SalesData.csv
```

was successfully stored within HDFS.

---

# Part 2: Performing MapReduce

---

# Understanding the Application Architecture

The solution uses the MapReduce design pattern.

Components:

```text
Driver
Mapper
Reducer
```

Each component performs a specific role.

---

# SalesCountryDriver.java

## Purpose

Controls and executes the Hadoop job.

Responsibilities:

- Configure Hadoop job
- Define Mapper
- Define Reducer
- Define input/output types
- Define HDFS paths
- Start execution

---

## Key Methods

### Set Job Name

```java
job_conf.setJobName("SalePerCountry");
```

---

### Configure Mapper

```java
job_conf.setMapperClass(
SalesCountry.SalesMapper.class
);
```

---

### Configure Reducer

```java
job_conf.setReducerClass(
SalesCountry.SalesCountryReducer.class
);
```

---

### Configure Input Path

```java
FileInputFormat.setInputPaths(...)
```

---

### Configure Output Path

```java
FileOutputFormat.setOutputPath(...)
```

---

### Run Job

```java
JobClient.runJob(job_conf);
```

---

# SalesMapper.java

## Purpose

Read input records and generate intermediate key-value pairs.

---

## Mapper Logic

Each sales record is:

```java
value.toString()
```

Then split:

```java
String[] record =
valueString.split(",");
```

---

## Country Extraction

The mapper extracts:

```java
record[7]
```

which contains the:

```text
Country
```

field.

---

## Mapper Output

Outputs:

```text
<Country,1>
```

Example:

```text
Canada → 1
Germany → 1
United States → 1
```

---

# Example

Input Data:

```text
Order 1, Canada
Order 2, Canada
Order 3, Germany
```

Mapper Output:

```text
<Canada,1>
<Canada,1>
<Germany,1>
```

---

# SalesCountryReducer.java

## Purpose

Aggregate all values associated with a country.

---

## Reducer Logic

Hadoop groups identical countries together:

```text
Canada {1,1}
Germany {1}
```

Reducer sums values.

---

## Example

Reducer Input:

```text
Canada {1,1}
```

Reducer Output:

```text
Canada 2
```

---

## Final Output

Produces:

```text
<Country,Total Sales Records>
```

---

# Step 5: Configure Environment Variables

Environment variables were required to compile and execute Hadoop Java applications.

---

## JAVA_HOME

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre/
```

Purpose:

Locate Java Runtime Environment.

---

## CLASSPATH

```bash
export CLASSPATH=...
```

Purpose:

Locate Hadoop libraries and project classes.

---

## Hadoop User Variables

```bash
export HDFS_NAMENODE_USER=root
```

```bash
export HDFS_DATANODE_USER=root
```

```bash
export HDFS_SECONDARYNAMENODE_USER=root
```

```bash
export YARN_RESOURCEMANAGER_USER=root
```

```bash
export YARN_NODEMANAGER_USER=root
```

Purpose:

Allow Hadoop services to run under the root user.

---

# Step 6: Compile Java Programs

## Command

```bash
javac -d . \
SalesMapper.java \
SalesCountryReducer.java \
SalesCountryDriver.java
```

---

## Result

Generated:

```text
SalesCountryDriver.class
SalesCountryReducer.class
SalesMapper.class
```

Location:

```text
SalesCountry/
```

---

# Why Compilation Is Required

Java source files:

```text
.java
```

must be converted into:

```text
.class
```

files before execution.

---

# Step 7: Create JAR File

## Command

```bash
jar cfm ProductSalePerCountry.jar \
Manifest.txt \
SalesCountry/*.class
```

---

## Result

Generated:

```text
ProductSalePerCountry.jar
```

---

# Why Use a JAR File?

A JAR:

```text
Java Archive
```

packages:

- Compiled classes
- Manifest
- Application logic

into a single executable file.

---

# Step 8: Execute MapReduce Job

## Command

```bash
hadoop jar \
ProductSalePerCountry.jar \
/inputMapReduce \
/mapreduce_output_sales
```

---

# Execution Flow

```text
SalesData.csv
      ↓
Mapper
      ↓
<Country,1>
      ↓
Shuffle & Sort
      ↓
Reducer
      ↓
<Country,Count>
      ↓
part-00000
```

---

# Job Statistics

Result:

```text
map 100%
reduce 100%
```

Output:

```text
Job completed successfully
```

Additional Statistics:

```text
Map Input Records = 999
Map Output Records = 999
Reduce Output Records = 58
```

Meaning:

```text
999 sales records
58 unique countries
```

---

# Step 9: Review Output

## Verify Output Folder

```bash
hdfs dfs -ls /mapreduce_output_sales
```

Output:

```text
_SUCCESS
part-00000
```

---

# Review Results

## Command

```bash
hdfs dfs -cat /mapreduce_output_sales/part-00000
```

Output Examples:

```text
Australia     38
Canada        76
France        27
Germany       25
Ireland       49
Netherlands   22
Spain         12
Sweden        13
```

---

# Understanding the Results

The reducer counted sales records by country.

Example:

```text
Canada 76
```

means:

```text
76 sales transactions
originated from Canada.
```

---

# HDFS Commands Used

Create directory:

```bash
hdfs dfs -mkdir /inputMapReduce
```

Upload file:

```bash
hdfs dfs -copyFromLocal SalesData.csv /inputMapReduce
```

List directory:

```bash
hdfs dfs -ls /inputMapReduce
```

View file:

```bash
hdfs dfs -cat /inputMapReduce/SalesData.csv
```

View results:

```bash
hdfs dfs -cat /mapreduce_output_sales/part-00000
```

---

# Hadoop Commands Used

Compile:

```bash
javac -d . \
SalesMapper.java \
SalesCountryReducer.java \
SalesCountryDriver.java
```

Create JAR:

```bash
jar cfm ProductSalePerCountry.jar \
Manifest.txt \
SalesCountry/*.class
```

Run Job:

```bash
hadoop jar \
ProductSalePerCountry.jar \
/inputMapReduce \
/mapreduce_output_sales
```

---

# Complete Data Pipeline

```text
Download Assignment Files
          ↓
Extract testprogram.zip
          ↓
Copy Files into NameNode
          ↓
Create HDFS Folder
          ↓
Upload SalesData.csv
          ↓
Compile Java Programs
          ↓
Create JAR File
          ↓
Execute MapReduce Job
          ↓
Generate Output
          ↓
Review Country Aggregation Results
```

---

# Real-World Applications

The same architecture can be used to:

### Retail Analytics

Count transactions by:

- Country
- Region
- Product

---

### Finance

Aggregate:

- Customer transactions
- Account activity
- Fraud indicators

---

### Telecommunications

Analyze:

- Call records
- Usage patterns

---

### Utilities

Analyze:

- Meter readings
- Work orders
- Maintenance activities
- Asset inspections

---

# Key Takeaways

1. Hadoop stores data using HDFS.
2. Docker simplifies Hadoop deployment.
3. Files must be loaded into HDFS before processing.
4. MapReduce provides distributed data processing.
5. The Mapper creates intermediate key-value pairs.
6. The Reducer aggregates grouped values.
7. Java programs can be used to create Hadoop applications.
8. JAR files package Hadoop applications for execution.
9. The MapReduce job processed 999 records and produced 58 country-level aggregates.
10. Hadoop successfully transformed raw transaction data into summarized analytical output.

---

# Skills Acquired

✅ HDFS Administration

✅ Hadoop CLI Operations

✅ Docker-Based Hadoop Management

✅ Java Compilation

✅ Hadoop MapReduce Development

✅ JAR File Creation

✅ Distributed Data Processing

✅ Big Data Analytics

✅ Country-Level Data Aggregation

✅ Hadoop Job Execution and Monitoring