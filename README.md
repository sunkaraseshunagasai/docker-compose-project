# docker-compose-project
# Docker Compose with Nginx Load Balancer for Python Applications

## 📌 Project Overview

Docker Compose does **not provide load balancing by default** when running multiple containers of the same application.

This project demonstrates how to:
- Use **Nginx as a reverse proxy and load balancer**
- Distribute incoming HTTP traffic across **multiple Python backend containers**
- Orchestrate everything using **Docker Compose**

Incoming requests hit **Nginx**, which then forwards traffic to multiple Python applications using a **round-robin load balancing strategy**.
----------------
## 🏗️ Architecture
### Request Flow
1. Client sends a request to the EC2 public IP on port **80**
2. Request reaches **Nginx Load Balancer**
3. Nginx distributes traffic across:
   - Backend 1 (Python App)
   - Backend 2 (Python App)
   - Backend 3 (Python App)
4. All services communicate over the **Docker internal network**

## 🧰 Tech Stack

- Docker
- Docker Compose
- Nginx (Load Balancer)
- Python (Backend Application)
- AWS EC2 (Optional – for deployment)


---

## ⚙️ Prerequisites

- Linux machine (Amazon Linux / RHEL / CentOS)
- Internet access
- EC2 Security Group allowing **port 80**

---

## 🚀 Setup Instructions

1️⃣ Install Docker
  yum install docker -y

2️⃣ Start and Enable Docker
  systemctl start docker
  systemctl enable docker
  docker --version
3️⃣ Install Docker Compose
  Install Docker Compose using the official installation script
  (The script file is available in this repository.)
  docker compose version(verifies installation).
4️⃣ Clone the Repository
  git clone <your-github-repo-url>
  cd <repository-folder-name>
5️⃣ Build and Run the Application
  docker compose up --build -d
✅ Verify Load Balancing

Open your browser and access:

http://<EC2-PUBLIC-IP>

To check logs:

docker compose logs -f nginx
🧹 Cleanup

To stop and remove containers:

docker compose down

**🎉 **Congratulations!** You have successfully completed this project and now understand how to implement load balancing in Docker Compose using Nginx.**
