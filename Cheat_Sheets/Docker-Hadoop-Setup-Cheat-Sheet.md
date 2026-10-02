# Docker Hadoop Setup Cheat Sheet

## Verify Docker

```bash
docker --version
```

---

## Start Hadoop Environment

```bash
docker compose up -d
```

---

## View Containers

```bash
docker ps
```

Expected:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

---

## Access NameNode

```bash
docker exec -it namenode bash
```

---

## Copy Files into NameNode

```bash
docker cp file.txt namenode:/input
```

or

```bash
docker cp testprogram namenode:/home
```

---

## Stop Containers

```bash
docker compose down
```

---

## Restart Containers

```bash
docker compose restart
```

---

## Verify Hadoop UI

NameNode:

```text
http://localhost:9870
```