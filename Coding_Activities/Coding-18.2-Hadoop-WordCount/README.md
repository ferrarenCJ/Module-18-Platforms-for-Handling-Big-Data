# Coding Activity 18.2: Executing the Word Count Program in Hadoop

**Course:** MIT Professional Education – Data Engineering Program  
**Module:** Module 18 – Platforms for Handling Big Data  
**Activity:** Required Coding Activity 18.2  
**Student:** Clifford Ferraren

---

# Objective

The objective of this activity was to use Hadoop's MapReduce framework to process a large real-world dataset. The dataset selected was the Project Gutenberg text version of *Moby Dick* by Herman Melville.

The activity demonstrated how to:

- Load data into Hadoop
- Store files in HDFS
- Execute a MapReduce Word Count job
- Analyze large text datasets
- Inspect Hadoop output results

This exercise provided hands-on experience with Hadoop's distributed storage and processing architecture.

---

# Environment

## Software Used

- Docker Desktop
- Docker Compose
- Hadoop
- HDFS
- YARN
- Git
- Visual Studio Code

---

## Hadoop Services Running

The Hadoop cluster consisted of the following services:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

All containers were verified to be in a healthy state prior to running the Word Count job.

---

# Dataset

## Source

Project Gutenberg

Book:

```text
Moby Dick
By Herman Melville
```

Downloaded as:

```text
Plain Text UTF-8
```

Local File:

```text
extracted.txt
```

Approximate Size:

```text
1.2 MB
```

The text file was used as input for the Hadoop Word Count application.

---

# Step 1: Verify Hadoop Containers

## Objective

Verify that all Hadoop services are running.

## Command Executed

```bash
docker ps
```

## Result

The Hadoop environment was running successfully.

Containers verified:

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

### Screenshot 1

Insert Screenshot:

```text
step1-hadoop-containers-running.png
```

---

# Step 2: Download and Extract Moby Dick

## Objective

Download a large text file for Hadoop processing.

## Source

Project Gutenberg

Book:

```text
Moby Dick
```

Downloaded as:

```text
Plain Text UTF-8
```

Resulting file:

```text
extracted.txt
```

The contents of the file were verified locally prior to uploading the file into Hadoop.

### Screenshot 2

Insert Screenshot:

```text
step2-mobydick-download.png
```

---

# Step 3: Create Input Folder in the NameNode Container

## Objective

Create a local staging location within the NameNode container.

## Command Executed

```bash
docker exec -it namenode bash
```

```bash
mkdir input
```

## Verification

```bash
ls
```

Output included:

```text
input
```

The local input directory was successfully created.

### Screenshot 3

Insert Screenshot:

```text
step3-create-input-folder.png
```

---

# Step 4: Copy the Text File to the NameNode Container

## Objective

Move the downloaded dataset into the Hadoop environment.

## Command Executed

```bash
docker cp extracted.txt namenode:/input/
```

## Verification

```bash
ls input
```

Output:

```text
extracted.txt
```

The file was successfully copied into the NameNode container.

### Screenshot 4

Insert Screenshot:

```text
step4-copy-file-to-container.png
```

---

# Step 5: Create an HDFS Input Folder

## Objective

Create an HDFS location to store the file for processing.

## Command Executed

```bash
hdfs dfs -mkdir -p /input
```

## Verification

```bash
hdfs dfs -ls /
```

Output:

```text
/input
/rmstate
/user
```

The HDFS input directory was successfully created.

### Screenshot 5

Insert Screenshot:

```text
step5-create-hdfs-input.png
```

---

# Step 6: Copy the Text File into HDFS

## Objective

Move the input file from the container filesystem into HDFS.

## Command Executed

```bash
hdfs dfs -put ./input/* /input
```

## Verification

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

The file was successfully uploaded into HDFS and became available for Hadoop processing.

### Screenshot 6

Insert Screenshot:

```text
step6-copy-to-hdfs.png
```

---

# Step 7: Download the Hadoop Word Count JAR

## Objective

Download the Word Count application required to execute the MapReduce job.

## Command Executed

```bash
curl -k -L https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar --output hadoop-mapreduce-examples-2.7.1-sources.jar
```

## Verification

```bash
ls
```

Output:

```text
hadoop-mapreduce-examples-2.7.1-sources.jar
```

The Word Count JAR file was successfully downloaded.

### Screenshot 7

Insert Screenshot:

```text
step7-download-jar.png
```

---

# Step 8: Execute the Word Count Program

## Objective

Execute a Hadoop MapReduce job against the Moby Dick dataset.

## Command Executed

```bash
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount /input /output
```

## Result

The Hadoop job executed successfully.

Key output:

```text
map 100%
reduce 100%
```

and

```text
Job completed successfully
```

Job statistics included:

```text
Map Input Records = 22312
Map Output Records = 215845
Reduce Output Records = 33572
```

These statistics confirmed that Hadoop successfully processed the entire text file.

### Screenshot 8

Insert Screenshot:

```text
step8-run-wordcount.png
```

---

# Step 9: Display the Results

## Objective

Review the output generated by Hadoop.

## Command Executed

```bash
hdfs dfs -cat /output/part-r-00000
```

## Result

The output file contained word frequencies generated by Hadoop.

Example results:

```text
wriggling     3
wrinkled      13
write         4
written       11
wrong         2
wrought       6
```

The results demonstrate Hadoop's ability to count and aggregate word occurrences in a large dataset.

### Screenshot 9

Insert Screenshot:

```text
step9-view-results.png
```

---

# Hadoop Processing Workflow

```text
Moby Dick Text File
          ↓
Copy to NameNode Container
          ↓
Create HDFS Input Folder
          ↓
Upload File to HDFS
          ↓
Download Word Count Program
          ↓
Execute MapReduce Job
          ↓
Map Phase
          ↓
Shuffle and Sort
          ↓
Reduce Phase
          ↓
Generate Output Results
          ↓
Display Results
```

---

# Verification Summary

| Step | Task | Status |
|--------|--------|--------|
| 1 | Verify Hadoop Containers Running | ✅ Complete |
| 2 | Download and Extract Moby Dick | ✅ Complete |
| 3 | Create Input Folder in NameNode Container | ✅ Complete |
| 4 | Copy File to NameNode Container | ✅ Complete |
| 5 | Create HDFS Input Folder | ✅ Complete |
| 6 | Copy File to HDFS | ✅ Complete |
| 7 | Download Word Count JAR | ✅ Complete |
| 8 | Execute Word Count Program | ✅ Complete |
| 9 | Display Output Results | ✅ Complete |

---

# Discussion

This activity demonstrated the complete Hadoop MapReduce workflow using a real-world dataset. The Moby Dick text file was loaded into HDFS and processed using the Hadoop Word Count application. During execution, Hadoop distributed the workload, created intermediate key-value pairs during the Map phase, grouped identical words during the Shuffle and Sort phase, and aggregated totals during the Reduce phase.

The job processed more than 223,000 word records and generated over 33,000 unique word counts. The successful execution illustrates Hadoop's capability to efficiently process and analyze large datasets.

---

# Conclusion

In this activity, Hadoop was successfully used to process a large text file using the MapReduce framework. The dataset was uploaded into HDFS, the Word Count application was executed successfully, and the resulting word frequencies were displayed from the Hadoop output directory.

The activity reinforced core Hadoop concepts including:

- HDFS file management
- Docker-based Hadoop deployment
- MapReduce execution
- Distributed data processing
- Big Data analytics workflows

This exercise demonstrated how Hadoop can transform large collections of unstructured text into structured analytical results.

---

# Key Concepts Learned

- Hadoop
- HDFS
- MapReduce
- Docker Containers
- YARN
- NameNode
- DataNode
- Word Count Processing
- Distributed Computing
- Big Data Analytics
- HDFS Commands
- Hadoop Job Execution