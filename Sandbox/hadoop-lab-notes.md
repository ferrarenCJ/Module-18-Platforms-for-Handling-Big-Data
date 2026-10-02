## Start Hadoop Cluster

```bash
docker compose up -d
```

## Verify Containers

```bash
docker ps
```

Expected containers:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```