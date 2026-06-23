# Velvet Restaurant Deployment (Phase 2)

🚀 **Dockerized App Deployment – Phase 2** This repository details Phase 2 of our deployment pipeline. It documents migrating the **Velvet Restaurant** static website onto an AWS EC2 Ubuntu instance, containerizing the application using Docker, resolving localized port binding infrastructure conflicts, and successfully serving the application to the public web.

---

## 📌 Project Overview

In this phase, we shifted from localized container testing to an active cloud environment. The web application is built on an lightweight, high-performance **Nginx Alpine** base image and served live over standard web traffic protocols via AWS.

* **Host OS:** Ubuntu 24.04 LTS (GNU/Linux 6.17.0-1007-aws x86_64)
* **Cloud Provider:** AWS EC2 (`us-east-2` Ohio)
* **Web Server / Base Image:** `nginx:alpine`
* **Live Instance IP:** `http://3.16.149.24`

---

## ⚙️ Architecture & Deployment Steps

### 1. Cloud Provisioning
An EC2 instance (`i-0979e8e9c915d14a2`) named **Hiring-Project-Server** was launched in `us-east-2` using an Ubuntu 24.04 LTS AMI. 

### 2. Environment Setup & Configuration
After establishing an SSH connection to the server, the codebase was structured under the `~/my-app` directory:
* `index.html` — Core web structure
* `style.css` — User interface styling
* `script.js` — Client-side interactions
* `Dockerfile` — Container assembly blueprint

### 3. Troubleshooting & Port Conflict Resolution
During the initial execution phase, an environmental issue arose where a host service was already bound to Port 80, throwing the following daemon failure:
```bash
docker: Error response from daemon: failed to create endpoint ... failed to bind host port for 0.0.0.0:80: address already in use.
