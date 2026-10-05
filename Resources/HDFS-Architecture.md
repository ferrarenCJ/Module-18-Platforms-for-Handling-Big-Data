# HDFS Architecture

## Hadoop Distributed File System

HDFS is Hadoop's distributed storage layer.

---

## Components

### NameNode

Stores metadata:

- File locations
- Block locations
- Directory structure

Acts as the master node.

---

### DataNode

Stores actual data blocks.

Acts as worker nodes.

---

## Replication

Default replication factor:

```text
3
```

Purpose:

- Fault tolerance
- High availability

---

## Workflow

```text
Client
   ↓
NameNode
   ↓
DataNodes
```

---

## Benefits

- Distributed storage
- Scalability
- Reliability
- Cost efficiency