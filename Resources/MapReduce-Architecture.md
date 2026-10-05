# MapReduce Architecture

## Purpose

MapReduce processes large datasets using distributed computing.

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

## Map Phase

Produces:

```text
<Key, Value>
```

Example:

```text
dog → <dog,1>
```

---

## Shuffle & Sort

Groups identical keys.

Example:

```text
dog {1,1}
cat {1}
```

---

## Reduce Phase

Aggregates grouped values.

Example:

```text
dog 2
cat 1
```

---

## Advantages

- Parallel processing
- Scalability
- Reliability
- Fault tolerance