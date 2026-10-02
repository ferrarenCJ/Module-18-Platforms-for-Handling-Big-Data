# MapReduce Cheat Sheet

## What Is MapReduce?

Distributed processing framework used by Hadoop.

Purpose:

```text
Process Large Datasets
```

---

## Workflow

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

## Mapper

Processes raw data.

Example:

Input:

```text
dog cat dog
```

Output:

```text
<dog,1>
<cat,1>
<dog,1>
```

---

## Shuffle & Sort

Groups matching keys:

```text
dog {1,1}
cat {1}
```

---

## Reducer

Aggregates values:

```text
dog 2
cat 1
```

---

## Word Count Example

Command:

```bash
hadoop jar hadoop-mapreduce-examples.jar \
org.apache.hadoop.examples.WordCount \
/input \
/output
```

---

## Sales Aggregation Example

Mapper Output:

```text
<Canada,1>
<Canada,1>
<Germany,1>
```

Reducer Output:

```text
Canada 2
Germany 1
```

---

## Benefits

- Parallel processing
- Scalability
- Fault tolerance
- Efficient large-scale analytics