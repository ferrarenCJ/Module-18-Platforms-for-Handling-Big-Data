# Coding Activity 18.1 Notes
# Setting Up Hadoop in a Docker Container

## Activity Overview

In this activity, Hadoop was deployed using Docker containers provided by the Big Data Europe Project. The objective was to create a fully functioning Hadoop environment, verify that all services were healthy, and confirm that the Hadoop Distributed File System (HDFS) web interface was accessible.

This hands-on exercise demonstrated how containerization simplifies Hadoop deployment and provides a reproducible environment for big data processing.

---

# Learning Outcome

✅ Set up Hadoop in a Docker container.

---

# Technologies Used

## Docker

Docker provides lightweight containers that package applications and dependencies together.

Benefits:

- Consistent deployment
- Easy configuration
- Isolation of services
- Faster setup compared to manual installation

---

## Docker Compose

Docker Compose automates deployment of multiple containers using a single configuration file.

Key file:

```text
docker-compose.yml
```

Purpose:

- Defines services
- Defines volumes
- Defines networking
- Defines dependencies

---

## Hadoop

Hadoop is an open-source framework used for:

- Distributed storage
- Distributed processing
- Big data analytics

Core components include:

- HDFS
- MapReduce
- YARN
- Hadoop Common

---

# Environment Setup

## Verify Docker Installation

Command:

```bash
docker --version
```

Result:

```text
Docker version 29.8.1
```

This verified Docker Desktop was installed and operational.

---

# Step 1: Review Existing Containers

Command:

```bash
docker ps
```

Purpose:

Displays all currently running Docker containers.

Initial Result:

```text
CONTAINER ID
IMAGE
COMMAND
CREATED
STATUS
PORTS
NAMES
```

No Hadoop containers were running prior to deployment.

### Concept Learned

Docker containers must be running before services become accessible.

---

# Step 2: Clone the Hadoop Repository

Repository:

```text
https://github.com/big-data-europe/docker-hadoop
```

Command:

```bash
git clone git@github.com:big-data-europe/docker-hadoop.git
```

Result:

```text
Cloning into 'docker-hadoop'
Receiving objects
Resolving deltas
```

The repository was successfully cloned to the local machine.

### Concept Learned

Git repositories often contain infrastructure-as-code configurations that allow environments to be reproduced quickly.

---

# Step 3: Locate docker-compose.yml

Commands:

```bash
cd docker-hadoop
```

```bash
dir
```

```bash
dir *.yml
```

*iles Found:

```text
docker-compos*.yml
docker-compose-v3.yml
```

##* Purpose

The docker*compose file contains the complete*configuration required to deploy t*e Hadoop environment.

### Concept*Learned

Docker Compose uses YAML *iles to define:

- Services
- Netw*rks
- Volumes
- Dependencies

---
*# Step 4: Deploy Hadoop Containers*
Command:

```bash
docker compose *p -d
```

Parameter:

```text
-d
`*`

Means:

```text
Detached Mode
`*`

*ontainers run in the background.

*--

## Services Created

The deplo*ment created:

```text
namenode
da*anode
resourcemanager
nodemanager
*istoryserver
```

*he following images were downloade*:

```text
bde2020/hadoop-namenode*bde2020/hadoop-datanode
bde*020/hadoop-resourcemanager
bde*020/hadoop-nodemanager
bde2020/had*op-historyserver
```

Docker*also created:

```text
Volumes
Net*orks
Containers
```

automatically*

### Concept Learned

Docker Comp*se enables the deployment of an en*ire Hadoop cluster using a single *ommand.

---

# Step 5: Verify Con*ainer Health

Command:

```bash*docker ps
```

Results:

```text*namenode      *Up (healthy)
datan*de       Up (healthy)
resourcemana*er Up (healthy)
nodem*nager    Up (healthy)
historyserve** Up (healthy)
```

### Why Healthy*Status Matters

Healthy status con*irms:

- Service*startup completed
- Required*ports are available
- Internal con*ainer checks passed
- Hadoop*services are functioning

### Conc*pt Learned

Container health check*