# Hadoop Commands Cheat Sheet

## Create HDFS Directory

```bash
hdfs dfs -mkdir /input
```

---

## Create Nested Directory

```bash
hdfs dfs -mkdir -p /input/data
```

---

## Upload File

```bash
hdfs dfs -put file.txt /input
```

---

## Copy Local File

```bash
hdfs dfs -copyFromLocal file.txt /input
```

---

## List Files

```bash
hdfs dfs -ls /
```

```bash
hdfs dfs -ls /input
```

---

## View File

```bash
hdfs dfs -cat /input/file.txt
```

---

## View First Lines

```bash
hdfs dfs -head /input/file.txt
```

---

## View Last Lines

```bash
hdfs dfs -tail /input/file.txt
```

---

## Remove File

```bash
hdfs dfs -rm /input/file.txt
```

---

## Remove Directory

```bash
hdfs dfs -rm -r /output
```

---

## Run Hadoop Job

```bash
hadoop jar program.jar input output
```