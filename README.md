Perfect 👍 — here’s a full **`README.md`** file for installing and testing **Jenkins on macOS using Docker**, including setup, verification, and cleanup steps.

---

````markdown
# ⚙️ Install Jenkins on macOS (Using Docker)

This guide walks you through installing and running **Jenkins** on macOS using **Docker Desktop**.

---

## 🧩 Prerequisites

Before starting, ensure you have:

- macOS **10.15 (Catalina)** or later  
- **Docker Desktop** installed and running 🐳  
  (If not installed, follow [Docker Installation Guide](./README.md) first)
- Stable internet connection

---

## 🚀 Step 1: Pull the Jenkins Docker Image

Open your terminal and run:

```bash
docker pull jenkins/jenkins:lts
````

This will download the **Long-Term Support (LTS)** version of Jenkins.

---

## 🏗️ Step 2: Run Jenkins in a Docker Container

Start a new Jenkins container:

```bash
docker run -d \
  --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

**Explanation:**

* `-d` → Run in detached mode (background)
* `--name jenkins` → Container name
* `-p 8080:8080` → Maps Jenkins web UI to port 8080
* `-p 50000:50000` → Port for agent connections
* `-v jenkins_home:/var/jenkins_home` → Persistent data volume

---

## 🔑 Step 3: Get the Initial Admin Password

Run the following command to retrieve the admin password:

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Copy this password — you’ll need it for first-time setup.

---

## 🌐 Step 4: Access Jenkins UI

Open your browser and go to:

👉 [http://localhost:8080](http://localhost:8080)

* Paste the **admin password** when prompted.
* Choose **Install suggested plugins** (recommended).
* Create your **admin user** when prompted.

---

## 🧪 Step 5: Verify Installation

Check running containers:

```bash
docker ps
```

You should see something like:

```
CONTAINER ID   IMAGE                 STATUS         PORTS
abcd1234efgh   jenkins/jenkins:lts   Up 2 minutes   0.0.0.0:8080->8080/tcp
```

Open Jenkins Dashboard → **Manage Jenkins → System Information**
✅ You should see your environment details and Docker as the runtime.

---

## 🧰 Step 6: Manage Jenkins

Stop Jenkins:

```bash
docker stop jenkins
```

Start Jenkins again:

```bash
docker start jenkins
```

Remove Jenkins container (if needed):

```bash
docker rm -f jenkins
```

Remove Jenkins volume (optional cleanup):

```bash
docker volume rm jenkins_home
```

---

## 🧭 Troubleshooting

* **Port already in use:**
  Change the port mapping:

  ```bash
  docker run -d -p 9090:8080 jenkins/jenkins:lts
  ```
* **Permission denied:**
  Use elevated privileges:

  ```bash
  sudo docker run ...
  ```
* **Docker daemon not running:**
  Ensure Docker Desktop is started before running Jenkins.

---

## ✅ Confirmation

After completing setup, you can install plugins or connect Jenkins with GitHub, Docker, AWS, or Kubernetes for CI/CD pipelines.

To test Jenkins builds:

1. Create a new **Freestyle Project**
2. Add a simple **"Execute Shell"** step:

   ```bash
   echo "Jenkins is running successfully!"
   ```
3. Click **Build Now** — you should see success ✅

---

**Author:** Deepak Prasad
**Last Updated:** October 2025

```

---

Would you like me to generate a downloadable `jenkins-setup-macos.md` file (so you can directly add it to your repo)?
```
