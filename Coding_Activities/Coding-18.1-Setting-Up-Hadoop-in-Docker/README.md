# Coding Activity 18.1: Setting Up Hadoop in a Docker Container

**Course:** MIT Professional Education - Data Engineering Program  
**Module:** Module 18 - Platforms for Handling Big Data  
**Activity:** Required Coding Activity 18.1  
**Student:** Clifford Ferraren  
**Date:** October 2026

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

The command successfully displayed the list of running Docker containers.

### Screenshot 1

**Insert Screenshot:**
`step1-docker-ps.png`

---

# Step 2: Clone the Big Data Europe Hadoop Repository

## Objective

Download the Hadoop Docker environment from the Big Data Europe project.

## Command Executed

```bash
git clone git@github.com:big-data-europe/docker-hadoop.git
```

## Result

The repository was successfully cloned to the local machine.

### Screenshot 2

**Insert Screenshot:**
`step2-git-clone.png`

---

# Step 3: Locate the Docker Compose File

## Objective

Verify the presence of the Docker Compose configuration file.

## Commands Executed

```bash
cd docker-hadoop
```

```bash
dir
```

```bash
dir *.yml
```

## Result

The repositor* contains the following Docker Com*ose files:

```text*docker-compose.yml
docker-compose-*3.yml
```

*he primary deployment*file required by the activity was *uccessfully identified.

### Scree*shot 3

**Insert Screenshot:**
`st*p3-docker-compose-file.png`

---

* Step 4: Create Hadoop Containers
*## Objective

Deploy the*Hadoop environment using Docker Co*pose.

## Command Executed

```bas*
docker compose up -d
```

## Resu*t

Docker successfully:

- Downloa*ed the Hadoop images
- Created the*required volumes
- Created the Had*op network
- Created the container*
- Started all Hadoop services

Co*tainers created:

```*ext
namenode
datanode
resourcemana*er
nodemanager
historyserver
```

*## Screenshot 4

**Insert*Screenshot:**
`step4-docker-compos*-up.png`

---

* Step 5: Verify Container Health

*# Objective

Confirm that*all Hadoop containers are running *nd healthy.

## Command Executed

*``bash
docker ps
```

## Result

A*l Hadoop services*reported a healthy status.

Verifi*d containers:

```text
namenode
da*an*de
resourcemanager
nodemanager
his*oryserver
```

*xample Status:

```text*Up 9 minutes *healthy)
```

This confirms that t*e Hadoop cluster services started *uccessfully and are operating norm*lly.

### Screenshot 5

**Insert S***enshot:**
`step5-healthy-contain*rs.png`

---

# Step 6: Access the*Hadoop Web Interface

## Objective*
Verify that the Hadoop NameNode w*b interface is available.

## URL *ccessed

```text
http://localhost:*870
```

## Result

The Hadoop Nam*Node web interface loaded successf*lly.

The interface displayed:

- *ameNode status
- Cluster summary
-*Storage capacity
- Live nodes
- Bl*ck information
- H*FS statistics

The webpage confirm*d that:

```*ext
namenode:9000 (active)
```

*nd*showed:

```text*Live Nodes: 1
Dead Nodes: 0
*``

*ndicating the Hadoop cluster was f*nctioning correctly.

### Screensh*t 6

**Insert Screenshot:**
`step6*hdfs-web-ui.png`

---

* Verification Summary

| Step | Ta*k | Status |
|--------|--------|--*-----|
| * | Review Docker containers | ✅ Co*plete |
| * | Clone Hadoop repository | ✅ Com*lete |
| 3 | Locate docker-compose*yml | ✅ Complete |
| 4 | Create Ha*oop containers | ✅ Complete |
| 5 * Verify healthy containers | ✅ Com*lete |
| 6 | Open Hadoop NameNode *I | ✅ Complete |

---

# Discussio*

This activity*demonstrated the process of deploy*ng Hadoop using Docker containers *nstead of performing a traditional*manual installation. Docker signif*cantly simplifies Hadoop deploymen* by packaging all required depende*cies into portable containers.

Th* Hadoop environment created during*this exercise consisted of the cor* services necessary to support dis*ributed storage and resource manag*ment within a Hadoop cluster. Usin* Docker Compose allowed*all services to be deployed with a*single command,*reducing setup complexity and ensu*ing consistent configuration.

Ver*fication through the Docker comman*-line tools and the Hadoop NameNod* web interface confirmed that the *luster was functioning correctly a*d was ready for future exercises i*volving HDFS and MapReduce.

---

* Conclusion

In this activity, a c*mplete Hadoop environment was succ*ssfully deployed using Docker cont*iners. The Hadoop Docker images we*e downloaded, the required contain*rs were created, all services reac*ed a healthy state, and the HDFS N*meNode web interface*was successfully accessed through * web browser.

The completed envir*nment provides a foundation for fu*ure Hadoop exercises, including st*ring data in HDFS, executing MapRe*uce jobs, and performing large-sca*e distributed data processing.

--*

# Key Concepts Learned

- Docker*Containers
- Docker Compose
- Hado*p Deployment
- HDFS (Hadoop Distri*uted File System)
- NameNode
- Dat*Node
- ResourceManager
- NodeManag*r
- Hadoop Cluster Architecture
- *istributed Storage
- Big Data Proc*ssing