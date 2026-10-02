# Final Assignment 18.1: Platforms for Handling Big Data

**Course:** MIT Professional Education – Data Engineering Program  
**Module:** Module 18 – Platforms for Handling Big Data  
**Assignment:** Required Final Assignment 18.1  
**Learning Outcome:** Write a Java program to access the Hadoop database.

---

# Objective

The objective of this assignment was to gain practical experience using Hadoop for distributed storage and distributed processing of data. The assignment involved loading a sales transaction dataset into the Hadoop Distributed File System (HDFS) and executing a Java-based MapReduce application to aggregate sales transactions by country.

The assignment was performed in two phases:

1. Ingesting data into HDFS.
2. Executing a Java MapReduce program to calculate sales counts by country.

---

# Environment

## Technologies Used

- Docker Desktop
- Hadoop 3.2.1
- HDFS
- YARN
- Java 8
- MapReduce
- Linux Command Line
- Visual Studio Code

---

## Hadoop Services

The Hadoop environment included the following containers:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

All services were running successfully before beginning the assignment.

---

# Assignment Files

The assignment package contained the following files:

```text
testprogram/
├── Manifest.txt
├── SalesCountryDriver.java
├── SalesMapper.java
├── SalesCountryReducer.java
└── SalesData.csv
```

---

# Part 1: Ingesting Data into HDFS

## Step 1: Extract testprogram.zip

### Objective

Extract the assignment package and verify its contents.

### Result

The ZIP archive was successfully extracted and the testprogram folder contained:

```text
Manifest.txt
SalesCountryDriver.java
SalesMapper.java
SalesCountryReducer.java
SalesData.csv
```

### Screenshot 1

Insert Screenshot:

```text
Part 1 - Step 1 - Extract testprogram.zip
```

---

## Step 2: Copy testprogram Folder to Hadoop NameNode

### Objective

Transfer the testprogram folder into the Hadoop NameNode container.

### Command

```bash
docker cp testprogram namenode:/home
```

### Verification

```bash
docker exec -it namenode bash
```

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
SalesMapper.java
SalesCountryReducer.java
SalesData.csv
```

### Screenshot 2

Insert Screenshot:

```text
Part 1 - Step 2 - Copy testprogram Folder to Hadoop NameNode
```

---

## Step 3: Create HDFS Folder and Upload SalesData.csv

### Objective

Create an HDFS input directory and load the sales dataset into Hadoop storage.

### Create HDFS Directory

```bash
hdfs dfs -mkdir /inputMapReduce
```

### Upload File

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

Insert Screenshot:

```text
Part 1 - Step 3 - Copy SalesData.csv into inputMapReduce
```

---

## Step 4: Verify SalesData.csv in HDFS

### Objective

Confirm that the file was successfully stored in HDFS.

### Commands

View beginning of file:

```bash
hdfs dfs -head /inputMapReduce/SalesData.csv
```

View end of file:

```bash
hdfs dfs -tail /inputMapReduce/SalesData.csv
```

### Result

The contents of the dataset were successfully displayed, confirming that the file was uploaded correctly into HDFS.

### Screenshot 4

Insert Screenshot:

```text
Part 1 - Step 4 - Verify SalesData.csv Using HDFS Cat
```

---

# Part 2: Performing MapReduce - Aggregation Sales by Country

## Java Program Descriptions

### SalesCountryDriver.java

SalesCountryDriver.java serves as the main controller and configuration class for the Hadoop MapReduce job. The driver creates the Hadoop job configuration, specifies the Mapper and Reducer classes, defines the key and value output types, configures the input and output paths, and submits the MapReduce job for execution.

Primary responsibilities:

- Create Hadoop job configuration.
- Register Mapper class.
- Register Reducer class.
- Configure input path.
- Configure output path.
- Execute MapReduce processing.

---

### SalesMapper.java

SalesMapper.java is the Mapper component responsible for processing each individual record in the SalesData.csv file.

The mapper:

1. Reads each sales transaction record.
2. Converts the row into a string.
3. Splits the record into individual fields using a comma delimiter.
4. Extracts the country field.
5. Emits a key-value pair in the format:

```text
<Country,1>
```

Example:

```text
Canada → <Canada,1>
Germany → <Germany,1>
United States → <United States,1>
```

These intermediate records are then passed to Hadoop's Shuffle and Sort phase.

---

### SalesCountryReducer.java

SalesCountryReducer.java is the Reducer component responsible for aggregating mapper results.

The reducer receives:

```text
Canada {1,1,1}
Germany {1,1}
Australia {1,1,1,1}
```

It sums the values for each country and generates the final result.

Example:

```text
Canada 3
Germany 2
Australia 4
```

The reducer produces the final sales transaction count by country.

---

## Step 5: Configure Hadoop Environment Variables

### Objective

Configure the environment required to compile and execute Hadoop Java applications.

### Commands

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre/
```

```bash
export CLASSPATH="$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-core-3.2.1.jar:$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-common-3.2.1.jar:$HADOOP_HOME/share/hadoop/common/hadoop-common-3.2.1.jar:~/testprogram/SalesCountry/*:$HADOOP_HOME/lib/*"
```

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

### Verification

```bash
echo $JAVA_HOME
```

Output:

```text
/usr/lib/jvm/java-8-openjdk-amd64/jre/
```

### Screenshot 5

Insert Screenshot:

```text
Part 2 - Step 2 - Configure Hadoop Environment Variables
```

---

## Step 6: Compile Java Programs

### Objective

Compile the Java source files into executable class files.

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

Insert Screenshot:

```text
Part 2 - Step 3 - Compile Java Files
```

---

## Step 7: Create ProductSalePerCountry.jar

### Objective

Package the compiled Java classes into an executable JAR file.

### Command

```bash
jar cfm ProductSalePerCountry.jar Manifest.txt SalesCountry/*.class
```

### Verification

```b*sh
ls -l ProductSalePerCountry.jar*```

Output:

```text
ProductSaleP*rCountry.jar
```

### Screenshot 7*
Insert Screenshot:

```text
Part * - Step 4 - Create ProductSalePerC*untry.jar
```

---

## Step 8: Exe*ute the MapReduce Job

### Objecti*e

Execute the Hadoop MapReduce ap*lication.

### Command

```bash
ha*oop jar ProductSalePerCountry.jar *inputMapReduce /mapreduce_output_s*les
```

### Result

The MapReduce*job completed successfully.

Outpu*:

```text
map 100%
reduce 100%
``*

and

```text
Job completed succe*sfully
```

### Job Statistics

``*text
Map Input Records = 999
Map O*tput Records = 999
Reduce Output R*cords = 58
```

Interpretation:

-*999 sales records processed.
- 58 *ountries identified.
- Aggregated *esults generated successfully.

##* Screenshot 8

Insert Screenshot:
*```text
Part 2 - Step 5 - Execute *ales Aggregation MapReduce Job
```*
---

## Step 9: Display Aggregati*n Results

### Objective

Review t*e output generated by the reducer.*
### Verify Output Files

```bash
*dfs dfs -ls /mapreduce_output_sale*
```

Output:

```text
_SUCCESS
pa*t-00000
```

### Display Results

*``bash
hdfs dfs -cat /mapreduce_ou*put_sales/part-00000
```

### Samp*e Results

```text
Argentina      *
Australia      38
Austria        *
Brazil         5
Canada         7*
France         27
Germany        *5
Ireland        49
Netherlands   *22
Spain          12
Sweden       * 13
```

The results represent the*number of sales transactions assoc*ated with each country.

### Scree*shot 9

Insert Screenshot:

```tex*
Part 2 - Step 6 - Display Sales A*gregation Results
```

---

# MapR*duce Workflow

```text
SalesData.csv
        ↓
Upload to HDFS
        ↓
SalesMapper.java
        ↓
<Country,1>
        ↓
Shuffle and Sort
        ↓
Group by Country
        ↓
SalesCountryReducer.java
        ↓
<Country,Total Transactions>
        ↓
part-00000
```

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

# Key Concepts Demonstrated

- Hadoop Distributed File System (HDFS)
- Java-Based MapReduce Development
- Distributed Data Processing
- Hadoop Job Configuration
- Data Aggregation
- Java Compilation
- JAR Packaging
- HDFS Administration
- Hadoop Command-Line Operations
- Big Data Analytics

---

# Conclusion

This assignment successfully demonstrated how Hadoop can be used for distributed storage and distributed processing of large datasets. The SalesData.csv dataset was ingested into HDFS, processed using a Java-based MapReduce application, and aggregated by country.

The Mapper extracted country information from individual sales records while the Reducer summed transaction counts for each country. The final output produced 58 country-level aggregates from 999 sales records.

This assignment reinforced practical experience with Hadoop, HDFS, MapReduce, Java development, JAR packaging, distributed analytics, and large-scale data processing workflows.