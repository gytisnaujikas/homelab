# 🏠 Homelab — Infrastructure, Cloud & DevOps

A hands-on homelab built to develop practical skills in **Linux administration, networking, containerization, automation, and cloud infrastructure**.

Hosted on Proxmox VE, this environment includes virtual machines, Docker workloads, private remote access, and an automated CI/CD pipeline.

## 🎯 Objectives

- Build and maintain a virtualized infrastructure.
- Develop Linux administration and networking skills.
- Deploy containerized applications using Docker Compose.
- Automate application builds, testing, and deployments.
- Practice secure remote administration.
- Explore Azure, Infrastructure as Code, and monitoring.

## 🏗️ Infrastructure Stack

| Component | Technology | Purpose |
|---|---|---|
| Virtualization | Proxmox VE 9 | Virtual machines and containers |
| Operating System | Ubuntu | Application hosting and Linux administration |
| Containers | Docker & Docker Compose | Containerized applications |
| Reverse Proxy | Nginx | Route HTTP requests to backend services |
| Backend | Python | Web application |
| CI/CD | GitHub Actions | Automated build, test, and deployment |
| Container Registry | GitHub Container Registry (GHCR) | Store Docker images |
| Remote Access | Tailscale & SSH | Private connectivity and administration |
| Media Server | Plex (LXC) | Separate media workload |
| Cloud | Microsoft Azure | Cloud administration learning |

## 🗺️ Architecture

```text
GitHub Repository
       |
       v
GitHub Actions
       |
       v
Build & Test Docker Image
       |
       v
GitHub Container Registry
       |
       v
Tailscale + SSH
       |
       v
Proxmox -> Ubuntu VM (docker01)
                    |
                    v
              Docker Compose
                    |
              +-----+-----+
              |           |
              v           v
            Nginx      Python Backend
```

## 🚀 Implemented Projects

### 1. Dockerized Web Application

**Technologies:** Docker, Docker Compose, Nginx, Python

- Deployed a Python backend in a Docker container.
- Configured Nginx as a reverse proxy.
- Connected services through Docker Compose networking.
- Used service-name DNS resolution for backend communication.
- Implemented a health endpoint.
- Practiced container lifecycle management and troubleshooting.

### 2. Automated CI/CD Pipeline

**Technologies:** Git, GitHub Actions, Docker, GHCR, SSH, Tailscale

The deployment workflow:

1. Push code changes to GitHub.
2. Trigger a GitHub Actions workflow.
3. Build and test the Docker image.
4. Publish the image to GHCR.
5. Connect to the homelab through Tailscale and SSH.
6. Pull the updated image and redeploy the application.

This project demonstrates practical experience with automated builds, container image publishing, and remote application deployment.

### 3. Docker Networking & Nginx

- Configured separate Docker Compose projects.
- Published services on different host ports.
- Practiced internal container communication.
- Used Nginx to forward requests to the Python backend.
- Troubleshot ports, connectivity, and application availability.

### 4. Virtualization & Remote Administration

- Manage virtual machines and Linux containers with Proxmox.
- Run Docker workloads on an Ubuntu VM.
- Maintain a separate Plex LXC container.
- Use SSH for remote administration.
- Use Tailscale for private connectivity.
- Practice Linux service, process, disk, memory, and network diagnostics.

## 🧰 Skills

- **Linux:** Services, processes, logs, storage, networking, troubleshooting
- **Networking:** IP addressing, DNS, routing, ports, reverse proxies
- **Containers:** Docker, Docker Compose, images, networking
- **CI/CD:** GitHub Actions, automated builds, testing, deployments
- **Version Control:** Git, branches, commits, merges
- **Remote Access:** SSH, Tailscale
- **Cloud:** Microsoft Azure fundamentals

## 🛣️ Roadmap

### Completed

- [x] Git and GitHub fundamentals
- [x] Docker and Docker Compose basics
- [x] Tailscale remote access and SSH
- [x] Docker networking
- [x] Homepage dashboard
- [x] Nginx reverse proxy
- [x] Containerized Python backend
- [x] GitHub Actions CI/CD pipeline
- [x] Docker image publishing to GHCR
- [x] Remote application deployment

### In Progress

- [ ] Linux administration and troubleshooting
- [ ] Microsoft Azure Administrator (AZ-104)
- [ ] Infrastructure documentation

### Planned

- [ ] Uptime Kuma — service availability monitoring
- [ ] Prometheus and Grafana — metrics and dashboards
- [ ] Ansible — configuration management
- [ ] Terraform — Infrastructure as Code
- [ ] Kubernetes — container orchestration
- [ ] Centralized logging
- [ ] Secrets management and security improvements

## 📚 Learning Approach

Each project focuses on understanding how the components work, how to troubleshoot problems, and how to improve reliability and maintainability.

The long-term goal is to build a documented, automated, and observable infrastructure environment that reflects practical Infrastructure, Cloud, and DevOps engineering workflows.

---

**Status:** Actively maintained and continuously evolving.
