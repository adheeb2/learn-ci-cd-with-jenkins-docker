# Day 1: Jenkins Configuration (with Docker)

Today we will learn how to configure **Jenkins locally using Docker**.  
By the end, you'll have Jenkins running on [http://localhost:8080](http://localhost:8080).

---

## 📌 Prerequisites

- [Docker installed](https://docs.docker.com/get-docker/) on your machine.
- Basic familiarity with running commands in a terminal.

---

## Step 1: Get the Jenkins Image

Head over to the official **Jenkins Docker Hub** page:  
👉 [Jenkins Docker Hub](https://hub.docker.com/r/jenkins/jenkins)

Look for the **latest LTS tag** (recommended, stable version). Example:

```
jenkins/jenkins:lts-jdk17
```

---

## Step 2: Run Jenkins in Docker

Open your terminal inside your project folder and run:

```bash
docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk17
```

What this does:

- `-p 8080:8080` → Exposes Jenkins UI at http://localhost:8080 by mapping lap's port 8080 with container's port 8080
- `-p 50000:50000` → Jenkins uses port 50000 to talk to “agents” (worker machines that do jobs).
- `-d`→ This is used to run in the background detached. So Jenkins keep running even after you close the terminal.
- `-v jenkins_home:/var/jenkins_home` → Saves Jenkins data so it persists
- `jenkins/jenkins:lts-jdk17` → Official stable Jenkins image with Java 17(As of this date)

---

## Step 3: Verify Jenkins is Running

Check if the container is running:

```bash
docker ps
```

If you see Jenkins listed, grab its container ID and check logs:

```bash
docker logs <container_id>
```

Scroll until you find the **Administrator Password**.

---

## Step 4: Access Jenkins

1. Open http://localhost:8080 in your browser.
2. Paste the Administrator Password from the logs.
3. Click **Install Suggested Plugins**.
4. Create your first **admin user**.

---

## Result

Congratulations user — Jenkins is now fully configured and running locally on Docker! You're ready to start creating your first Jenkins jobs and pipelines.

---
