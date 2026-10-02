# Coding Activity 18.2: Executing the Word Count Program in Hadoop

**Course:** MIT Professional Education - Data Engineering Program  
**Module:** Module 18 - Platforms for Handling Big Data  
**Activity:** Required Coding Activity 18.2  
**Student:** Clifford Ferraren

---

# Objective

The objective of this activity was to use Hadoop's MapReduce framework to execute a Word Count program against a larger dataset. The dataset used was the Project Gutenberg text version of *Moby Dick* by Herman Melville.

The activity demonstrates how Hadoop processes large text files using:

- HDFS
- MapReduce
- Dockerized Hadoop Services

---

# Step 1: Verify Hadoop Containers

## Command

```bash
docker ps
```

## Result

Verified that all Hadoop containers were running.

Containers:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

All containers reported:

```text
healthy
```

### Screenshot 1

Insert:

```text
step1-hadoop-containers-running.png
```

---

# Step 2: Download Moby Dick Dataset

## Source

Project Gutenberg

Book:

```text
Moby Dick
Herman Melville
```

Downloaded:

```text
2701-0.zip
```

Extracted:

```text
2701-0.txt
```

## Result

Successfully downloaded and extracted the text file.

### Screenshot 2

Insert:

```text
step2-mobydick-download.png
```

---

# Step 3: Create Input Folder in the NameNode Container

## Enter Container

```bash
docker exec -it namenode bash
```

## Create Folder

```bash
mkdir input
```

## Verify

```bash
ls
```

Output:

```text
input
```

### Screenshot 3

Insert:

```text
step3-create-input-folder.png
```

---

# Step 4: Copy the Moby Dick Text File to the NameNode Container

## Command

Example:

```bash
docker cp "C:\Downloads\2701-0.txt" namenode:/input/
```

## Verify

Inside container:

```bash
ls input
```

Output:

```text
2701-0.txt
```

### Screenshot 4

Insert:

```text
step4-copy-file-to-container.png
```

---

# Step 5: Create an HDFS Input Folder

## Command

```bash
hadoop fs -mkdir -p input
```

## Verify

```bash
hdfs dfs -ls
```

Output:

```text
input
```

### Screenshot 5

Insert:

```text
step5-create-hdfs-input.png
```

---

# Step 6: Copy the Text File from the Container to HDFS

## Command

```bash
hdfs dfs -put ./input/* input
```

## Verify

```bash
hdfs dfs -ls input
```

Output:

```text
2701-0.txt
```

### Screenshot 6

Insert:

```text
step6-copy-to-hdfs.png
```

---

# Step 7: Download the Hadoop Word Count JAR

## Command

```bash
curl -L \
https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar \
--output hadoop-mapreduce-examples-2.7.1-sources.jar
```

## Verify

```bash
ls
```

Output:

```text
hadoop-mapreduce-examples-2.7.1-sources.jar
```

### Screenshot 7

Insert:

```text
step7-download-jar.png
```

---

# Step 8: Execute the Word Count Program

## Cleanup

If output already exists:

```bash
hdfs dfs -rm -r output
```

or

```bash
rm -r output
```

## Run Job

```bash
hadoop jar \
hadoop-mapreduce-examples-2.7.1-sources.jar \
org.apache.hadoop.examples.WordCount \
input \
output
```

## Result

MapReduce executed successfully.

Generated:

```text
output/
```

and

```text
_SUCCESS
```

### Screenshot 8

Insert:

```text
step8-run-wordcount.png
```

---

# Step 9: Display the Output

## Command

```bash
hdfs dfs -cat output/part-r-00000
```

## Result

Displayed the final word-frequency counts from Moby Dick.

Example:

```text
whale      xxxx
captain    xxxx
ship       xxxx
sea        xxxx
```

Actual counts vary based on the source file.

### Screenshot 9

Insert:

```text
step9-view-results.png
```

---

# Hadoop Processing Flow

```text
Moby Dick Text File
          ↓
Copy to NameNode Container
          ↓
Upload to HDFS
          ↓
Word Count Job
          ↓
Map Phase
          ↓
Shuffle and Sort
          ↓
Reduce Phase
          ↓
Output Results
```

---

# Verification Summary

| Step | Description | Status |
|--------|--------|--------|
| 1 | Verify Hadoop Containers | ✅ |
| 2 | Download Moby Dick | ✅ |
| 3 | Create Input Folder | ✅ |
| 4 | Copy File to Container | ✅ |
| 5 | Create HDFS Input Folder | ✅ |
| 6 | Upload File to HDFS | ✅ |
| 7 | Download WordCount JAR | ✅ |
| 8 | Execute WordCount | ✅ |
| 9 | Display Results | ✅ |

---

# Conclusion

This activity demonstrated how Hadoop and MapReduce process large text datasets. The Moby Dick text file was uploaded to HDFS, processed using the Hadoop Word Count example application, and the resulting word frequencies were generated through a distributed MapReduce job.

The activity reinforced concepts related to:

- HDFS
- MapReduce
- Dockerized Hadoop
- Word Count Processing
- Distributed Computing
- Big Data Analytics