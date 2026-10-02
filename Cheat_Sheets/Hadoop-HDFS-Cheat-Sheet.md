# Hadoop HDFS Cheat Sheet

## What Is HDFS?

Hadoop Distributed File System.

Purpose:

```text
Distributed Storage
```

---

## HDFS Components

### NameNode

Stores:

- Metadata
- Block locations
- File structure

Acts as:

```text
Master Node
```

---

### DataNode

Stores:

- Data blocks

Acts as:

```text
Worker Node
```

---

## Replication

Default:

```text
3
```

Purpose:

- Fault tolerance
- High availability

---

## HDFS Workflow

```text
Client
   ↓
NameNode
   ↓
DataNodes
```

---

## Common Commands

```bash
hdfs dfs -mkdir /input
```

```bash
hdfs dfs -put file.txt /input
```

```bash
hdfs dfs -ls /
```

```bash
hdfs dfs -cat /input/file.txt
```

---

## Benefits

- Scalable
- Distributed
- Fault tolerant
- Cost effective