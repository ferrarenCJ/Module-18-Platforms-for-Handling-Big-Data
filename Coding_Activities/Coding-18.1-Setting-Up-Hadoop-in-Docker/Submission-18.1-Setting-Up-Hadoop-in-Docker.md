# Coding Activity 18.1: Setting Up Hadoop in a Docker Container

## Objective

Create a Hadoop Docker environment using the Big Data Europe Hadoop project and verify that the Hadoop services are operating correctly.

---

# Step 1: Review Existing Docker Containers

Command:

```bash
docker ps
```

Result:

Reviewed the list of currently running Docker containers on the local machine.

### Screenshot

Insert Screenshot:

`step1-docker-ps.png`

---

# Step 2: Clone the Big Data Europe Hadoop Repository

Repository:

```text
https://github.com/big-data-europe/docker-hadoop.git
```

Command:

```bash
git clone https://github.com/big-data-europe/docker-hadoop.git
```

Result:

Successfully cloned the Hadoop Docker repository.

### Screenshot

Insert Screenshot:

`step2-git-clone.png`

---

# Step 3: Locate docker-compose.yml

Navigate to the repository.

Command:

```bash
cd docker-hadoop
ls
```

Result:

Verified that the repository contains the required:

```text
docker-compose.yml
```

file.

### Screenshot

Insert Screenshot:

`step3-docker-compose-file.png`

---

# Step 4: Create Hadoop Containers

Command:

```bash
docker-compose up -d
```

Result:

Hadoop containers were successfully created and started in detached mode.

### Screenshot

Insert Screenshot:

`step4-docker-compose-up.png`

---

# Step 5: Verify Container Health

Command:

```bash
docker ps
```

Result:

Verified that all Hadoop containers are running.

Expected status:

```text
healthy
```

### Screenshot

Insert Screenshot:

`step5-healthy-containers.png`

---

# Step 6: Verify Hadoop Web Interface

Open browser:

```text
http://localhost:9870
```

Result:

Successfully accessed the Hadoop HDFS NameNode web interface.

### Screenshot

Insert Screenshot:

`step6-hdfs-web-ui.png`

---

# Summary

This activity demonstrated how to:

- Clone a Hadoop Docker project.
- Deploy Hadoop using Docker containers.
- Verify healthy container status.
- Access the Hadoop HDFS web interface.
- Validate a functioning Hadoop environment.

The Hadoop deployment included HDFS and YARN services running inside Docker containers, providing a foundation for executing Hadoop jobs in later activities.