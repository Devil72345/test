# 🐳 Install Docker on macOS

This guide explains how to install **Docker Desktop** on macOS and verify your installation using a test container.

---

## 🧩 Prerequisites

- macOS **10.15 (Catalina)** or later  
- Minimum **4 GB RAM**  
- **Admin privileges** on your system

---

## ⚙️ Step 1: Download and Install Docker Desktop

1. Visit the official Docker download page:  
   👉 [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

2. Download the **Mac (Apple Silicon)** or **Mac (Intel Chip)** version depending on your hardware.

3. Open the downloaded `.dmg` file and **drag Docker to the Applications folder**.

4. Launch Docker Desktop from **Applications** or **Spotlight Search**.

5. Once Docker starts, you’ll see a 🐳 whale icon in the macOS status bar.

---

## 🧪 Step 2: Verify Installation

Open your terminal and run:

```bash
docker --version
