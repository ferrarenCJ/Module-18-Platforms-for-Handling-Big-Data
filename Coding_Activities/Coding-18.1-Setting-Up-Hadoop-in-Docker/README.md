# Coding Activity 18.1: Setting Up Hadoop in a Docker Container

**Course:** MIT Professional Education - Data Engineering Program  
**Module:** Module 18 - Platforms for Handling Big Data  
**Activity:** Required Coding Activity 18.1  
**Student:** Clifford Ferraren

---

# Objective

The objective of this activity was to create a Hadoop environment using Docker containers, verify that all Hadoop services started successfully, and confirm that the Hadoop Distributed File System (HDFS) web interface was accessible through a web browser.

---

# Environment

## Software Used

- Docker Desktop
- Docker Compose
- Git
- Hadoop Docker Images (Big Data Europe Project)

## Repository

```text
https://github.com/big-data-europe/docker-hadoop
```

## Hadoop Components Deployed

- NameNode
- DataNode
- ResourceManager
- NodeManager
- HistoryServer

---

# Step 1: Review Existing Docker Containers

## Objective

Review any containers currently running on the local machine.

## Command Executed

```bash
docker ps
```

## Result

The command successfully displayed the list of running Docker containers. Prior to deployment, no Hadoop containers were running.

### Screenshot 1

Insert Screenshot:

```text
step1-docker-ps.png
```

---

# Step 2: Clone the Big Data Europe Hadoop Repository

## Objective

Download the Hadoop Docker environment from the Big Data Europe project.

## Command Executed

```bash
git clone git@github.com:big-data-europe/docker-hadoop.git
```

## Result

The Hadoop Docker repository was successfully cloned to the local machine.

Example output:

```text
Cloning into 'docker-hadoop'...
Receiving objects: 100%
Resolving deltas: 100%
```

### Screenshot 2

Insert Screenshot:

```text
step2-git-clone.png
```

---

# Step 3: Locate the Docker Compose File

## Objective

Verify the presence of the Docker Compose configuration file used to deploy the Hadoop environment.

## Commands Executed

```bash
cd docker-hadoop
```

```bash
dir
```

## Result

The repository contains the required Docker Compose configuration files:

```text
docker-compose.yml
docker-compose-v3.yml
```

The primary deployment file, `docker-compose.yml`, was successfully identified.

### Screenshot 3

Insert Screenshot:

```text
step3-docker-compose-file.png
```

---

# Step 4: Create Hadoop Containers

## Objective

Deploy the Hadoop environment using Docker Compose.

## Command Executed

```bash
docker compose up -d
```

## Explanation

The `-d` parameter runs the containers in detached mode, allowing the services to run in the background.

## Result

Docker successfully:

- Downloaded the required Hadoop images
- Created the Docker network
- Created the Docker volumes
- Created all Hadoop containers
- Started all Hadoop services

Containers created:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

### Screenshot 4

Insert Screenshot:

```text
step4-docker-compose-up.png
```

---

# Step 5: Verify Container Health

## Objective

Verify that all Hadoop services are running correctly.

## Command Executed

```bash
docker ps
```

## Result

All Hadoop containers displayed a healthy status.

Verified services:

```text
namenode
datanode
resourcemanager
nodemanager
historyserver
```

Example status:

```text
Up 9 minutes (healthy)
```

This confirmed that the Hadoop cluster started successfully and all services were operating normally.

### Screenshot 5

Insert Screenshot:

```text
step5-healthy-containers.png
```

---

# Step 6: Access the Hadoop Web Interface

## Objective

Verify that the Hadoop NameNode web interface is accessible.

## URL Accessed

```text
http://localhost:9870
```

## Result

The Hadoop HDFS NameNode web interface loaded successfully.

The page displayed:

- NameNode Overview
- Cluster Summary
- DFS Capacity
- Live Nodes
- Block Information
- HDFS Statistics

The dashboard confirmed:

```text
namenode:9000 (active)
```

and showed:

```text
Live Nodes: 1
Dead Nodes: 0
```

indicating that the Hadoop cluster was functioning correctly.

### Screenshot 6

Insert Screenshot:

```text
step6-hdfs-web-ui.png
```

---

# Verification Summary

| Step | Task | Status |
|--------|--------|--------|
| 1 | Review Docker containers | ✅ Complete |
| 2 | Clone Hadoop repository | ✅ Complete |
| 3 | Locate docker-compose.yml | ✅ Complete |
| 4 | Create Hadoop containers | ✅ Complete |
| 5 | Verify healthy containers | ✅ Complete |
| 6 | Access Hadoop NameNode UI | ✅ Complete |

---

# Discussion

This activity demonstrated how Hadoop can be rapidly deployed using Docker containers instead of a traditional manual installation. Docker Compose simplified the deployment process by automatically creating multiple Hadoop services and their associated networking configurations.

The deployed environment consisted of the core Hadoop services required for distributed storage and resource management. Verification using both Docker commands and the HDFS NameNode web interface confirmed that the Hadoop cluster was operating correctly.

This environment now provides a foundation for future Hadoop exercises involving HDFS storage, MapReduce processing, and distributed data analytics.

---

# Conclusion

A fully operational Hadoop environment was successfully deployed using Docker containers. The Hadoop Docker images were downloaded, all required containers were created, container health was verified, and the Hadoop HDFS NameNode interface was successfully accessed through a web browser.

This activity provided practical experience with containerized Hadoop deployment and demonstrated the relationship between Docker, HDFS, and distributed computing environments.

---

# Key Concepts Learned

- Docker Containers
- Docker Compose
- Hadoop Deployment
- Hadoop Distributed File System (HDFS)
- NameNode
- DataNode
- ResourceManager
- NodeManager
- HistoryServer
- Distributed Storage
- Big Data Infrastructure
- Hadoop Cluster Administration