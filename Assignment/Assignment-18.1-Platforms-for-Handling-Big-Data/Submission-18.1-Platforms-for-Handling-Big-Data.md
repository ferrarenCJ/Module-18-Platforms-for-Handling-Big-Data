# Required Final Assignment 18.1: Platforms for Handling Big Data

**Course:** MIT Professional Education – Data Engineering Program  
**Module:** Module 18 – Platforms for Handling Big Data  
**Assignment:** Required Final Assignment 18.1  
**Learning Outcome Addressed:** Write a Java program to access the Hadoop database.

---

# Introduction

The objective of this assignment was to gain practical experience using Hadoop for distributed data storage and distributed data processing. The assignment involved loading a sales dataset into the Hadoop Distributed File System (HDFS) and executing a Java-based MapReduce application to aggregate sales transactions by country.

The assignment was completed in two parts:

1. Ingesting data into HDFS.
2. Performing MapReduce aggregation using Java programs.

---

# Part 1: Ingesting Data into the HDFS

## Step 1: Extract testprogram.zip

The provided ZIP archive was successfully downloaded and extracted.

The extracted folder contained:

```text
testprogram
├── Manifest.txt
├── SalesCountryDriver.java
├── SalesMapper.java
├── SalesCountryReducer.java
└── SalesData.csv
```

### Screenshot 1

**Part 1 - Step 1 - Extract testprogram.zip**

> Insert Screenshot Here

---

## Step 2: Copy testprogram Folder to Hadoop NameNode

The testprogram folder was copied from the local machine into the Hadoop NameNode container using Docker.

### Command

```bash
docker cp testprogram namenode:/home
```

### Verification

```bash
cd /home
ls
```

Output:

```text
testprogram
```

Contents verified:

```text
Manifest.txt
SalesCountryDriver.java
SalesMapper.java
SalesCountryReducer.java
SalesData.csv
```

### Screenshot 2

**Part 1 - Step 2 - Copy testprogram Folder to Hadoop NameNode**

> Insert Screenshot Here

---

## Step 3: Copy SalesData.csv into HDFS

An input directory named `inputMapReduce` was created in HDFS and the sales dataset was uploaded.

### Create HDFS Directory

```bash
hdfs dfs -mkdir /inputMapReduce
```

### Upload Dataset

```bash
hdfs dfs -copyFromLocal SalesData.csv /inputMapReduce
```

### Verification

```bash
hdfs dfs -ls /inputMapReduce
```

Output:

```text
/inputMapReduce/SalesData.csv
```

### Screenshot 3

**Part 1 - Step 3 - Copy SalesData.csv into inputMapReduce**

> Insert Screenshot Here

---

## Step 4: Verify SalesData.csv Using HDFS Commands

The uploaded file was verified using HDFS commands.

### Commands

```bash
hdfs dfs -head /inputMapReduce/SalesData.csv
```

```bash
hdfs dfs -tail /inputMapReduce/SalesData.csv
```

### Result

The contents of the dataset were successfully displayed, confirming that the file was stored in HDFS.

### Screenshot 4

**Part 1 - Step 4 - Verify SalesData.csv Using HDFS Cat**

> Insert Screenshot Here

---

# Part 2: Performing MapReduce - Aggregation Sales by Country

## Description of Java Files

### SalesCountryDriver.java

SalesCountryDriver.java serves as the main driver program for the Hadoop MapReduce job. The driver creates and configures the Hadoop job, defines the Mapper and Reducer classes, specifies the input and output data types, identifies the HDFS input and output locations, and submits the job for execution.

Key responsibilities include:

- Configure the Hadoop job.
- Register the Mapper class.
- Register the Reducer class.
- Define input and output locations.
- Execute the MapReduce application.

---

### SalesMapper.java

SalesMapper.java is the Mapper component responsible for processing each sales transaction record from the SalesData.csv dataset. The mapper reads each line of data, converts it into a string, separates the record into fields, extracts the country value, and emits an intermediate key-value pair.

Mapper output:

```text
<Country,1>
```

Example:

```text
<Canada,1>
<Canada,1>
<Germany,1>
```

The output is then passed to the Hadoop Shuffle and Sort phase.

---

### SalesCountryReducer.java

SalesCountryReducer.java is the Reducer component responsible for aggregating all mapper outputs belonging to the same country.

The reducer receives grouped country records:

```text
Canada {1,1,1}
Germany {1,1}
```

It then sums the values and produces the final country totals.

Reducer output:

```text
Canada 3
Germany 2
```

The reducer generates the final sales transaction count for each country within the dataset.

---

## Step 5: Configure Hadoop Environment Variables

Environment variables were configured to support compilation and execution of Hadoop Java applications.

### Commands

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre/
```

```bash
export CLASSPATH="$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-core-3.2.1.jar:$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-common-3.2.1.jar:$HADOOP_HOME/share/hadoop/common/hadoop-common-3.2.1.jar:~/testprogram/SalesCountry/*:$HADOOP_HOME/lib/*"
```

```bash
export HDFS_NAMENODE_USER=root
export HDFS_DATANODE_USER=root
export HDFS_SECONDARYNAMENODE_USER=root
export YARN_RESOURCEMANAGER_USER=root
export YARN_NODEMANAGER_USER=root
```

### Verification

```bash
echo $JAVA_HOME
```

Output:

```text
/usr/lib/jvm/java-8-openjdk-amd64/jre/
```

### Screenshot 5

**Part 2 - Step 2 - Configure Hadoop Environment Variables**

> Insert Screenshot Here

---

## Step 6: Compile Java Programs

The Java source files were compiled into executable class files.

### Command

```bash
javac -d . SalesMapper.java SalesCountryReducer.java SalesCountryDriver.java
```

### Verification

```bash
ls SalesCountry
```

Output:

```text
SalesCountryDriver.class
SalesCountryReducer.class
SalesMapper.class
```

### Screenshot 6

**Part 2 - Step 3 - Compile Java Files**

> Insert Screenshot Here

---

## Step 7: Create the JAR File

The compiled Java classes were packaged into a Hadoop executable JAR file.

### Command

```bash
jar cfm ProductSalePerCountry.jar Manifest.txt SalesCountry/*.class
```

### Verification

```bash
ls -l ProductSalePerCountry.jar
```

Output:

```text
ProductSalePerCountry.jar
```

### Screenshot 7

**Part 2 - Step 4 - Create ProductSalePerCountry.jar**

> Insert Screenshot Here

---

## Step 8: Execute the MapReduce Job

The Hadoop MapReduce job was executed to aggregate sales records by country.

### Command

```bash
hadoop jar ProductSalePerCountry.jar /inputMapReduce /mapreduce_output_sales
```

### Result

The job completed successfully.

Output:

```text
map 100%
reduce 100%
```

and

```text
Job completed successfully
```

### Job Statistics

```text
Map Input Records = 999
Map Output Records = 999
Reduce Output Records = 58
```

The job processed 999 sales records and produced summarized results for 58 countries.

### Screenshot 8

**Part 2 - Step 5 - Execute Sales Aggregation MapReduce Job**

> Insert Screenshot Here

---

## Step 9: Review MapReduce Output

The output directory generated by Hadoop was verified.

### Verify Output Files

```bash
hdfs dfs -ls /mapreduce_output_sales
```

Output:

```text
_SUCCESS
part-00000
```

### Display Results

```bash
hdfs dfs -cat /mapreduce_output_sales/part-00000
```

### Sample Results

```text
Argentina     1
Australia     38
Austria       7
Brazil        5
Canada        76
France        27
Germany       25
Ireland       49
Netherlands   22
Spain         12
Sweden        13
```

The results show the total number of sales transactions associated with each country in the dataset.

### Screenshot 9

**Part 2 - Step 6 - Display Sales Aggregation Results**

> Insert Screenshot Here

---

# Results Summary

| Metric | Result |
|----------|----------|
| Input Dataset | SalesData.csv |
| Records Processed | 999 |
| Mapper Output Records | 999 |
| Unique Countries | 58 |
| Reducer Output Records | 58 |
| Map Tasks | 2 |
| Reduce Tasks | 1 |
| Job Status | Successful |

---

# Conclusion

This assignment demonstrated the complete Hadoop workflow for big data storage and processing. The SalesData.csv dataset was successfully loaded into HDFS and analyzed using a Java-based Hadoop MapReduce application. The Mapper extracted country information from individual sales records, while the Reducer aggregated transaction counts by country.

The assignment reinforced practical skills related to:

- Hadoop Distributed File System (HDFS)
- Docker-based Hadoop deployment
- Java MapReduce development
- Java compilation and JAR creation
- Hadoop job execution
- Distributed data processing
- Sales data aggregation and analytics

The successful execution of the MapReduce application illustrates how Hadoop can efficiently transform raw transactional data into meaningful summarized business information.