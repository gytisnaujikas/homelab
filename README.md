🏠 Homelab — Infrastructure, Cloud & DevOps

A hands-on homelab built to develop practical skills in Linux administration, networking, containerization, automation, and cloud infrastructure.

The environment runs on Proxmox VE and includes Docker workloads, private remote access, version-controlled configuration, and an automated CI/CD pipeline. It serves as a practical learning environment for my transition toward Infrastructure, Cloud, and DevOps Engineering.

Rather than just following tutorials, I use this environment to build, test, troubleshoot, document, and improve real infrastructure projects.

🎯 Objectives

Build and maintain a virtualized infrastructure.

Develop practical Linux administration and networking skills.

Deploy and manage containerized applications with Docker Compose.

Automate application builds, testing, and deployments.

Practice secure remote administration and private networking.

Explore cloud infrastructure, Infrastructure as Code (IaC), and monitoring.

Document projects and technical decisions in a version-controlled repository.

🏗️ Infrastructure Overview

The homelab is hosted on a Lenovo ThinkCentre M70q running Proxmox VE.

Component

Technology

Purpose

Virtualization

Proxmox VE 9

Host and manage virtual machines and containers

Application environment

Ubuntu VM (docker01)

Run Docker workloads and deployment services

Containerization

Docker & Docker Compose

Package and manage applications

Reverse proxy

Nginx

Route HTTP requests to application services

Application backend

Python

Serve a containerized web application

CI/CD

GitHub Actions

Build, test, and publish application images

Container registry

GitHub Container Registry (GHCR)

Store versioned Docker images

Remote access

Tailscale & SSH

Access infrastructure remotely

Media services

Plex in an LXC container

Run a separate media server workload

Cloud learning

Microsoft Azure

Develop cloud administration skills

🗺️ Architecture

The following diagram illustrates the main components and the application deployment workflow.

flowchart TB
    subgraph Host["Proxmox VE Host"]
        subgraph VM["Ubuntu VM — docker01"]
            subgraph Docker["Docker Compose"]
                NGINX["Nginx Reverse Proxy"]
                APP["Python Backend"]
                NGINX --> APP
            end
        end
        PLEX["Separate Plex LXC"]
    end

    USER["Client / Browser"] -->|"HTTP :8082"| NGINX

    DEV["Code Changes"] --> GH["GitHub Repository"]
    GH --> CI["GitHub Actions"]
    CI --> TEST["Build & Test"]
    TEST --> REG["GitHub Container Registry"]
    REG -->|"Tailscale + SSH"| DEPLOY["Deployment on docker01"]
    DEPLOY --> Docker

The application is split into separate containers. Nginx receives HTTP requests and forwards them to the Python backend through the Docker Compose network.

The deployment pipeline builds and tests the backend image, publishes it to GHCR, and connects to the homelab over Tailscale and SSH to pull and deploy the updated version.

🚀 Implemented Projects

1. Dockerized Web Application

Technologies: Docker, Docker Compose, Nginx, Python

Deployed a Python backend as a Docker container.

Configured Nginx as a reverse proxy.

Connected application services using Docker Compose networking and service-name DNS resolution.

Published the application through a host port.

Implemented a health endpoint for basic application checks.

Practiced container logs, lifecycle management, and troubleshooting.

2. Automated CI/CD Pipeline

Technologies: Git, GitHub Actions, Docker, GHCR, SSH, Tailscale

Implemented an end-to-end application deployment workflow:

Make and push code changes to GitHub.

Trigger a GitHub Actions workflow.

Build the Docker image and run automated checks.

Publish the image to GitHub Container Registry.

Connect to the homelab deployment environment over Tailscale and SSH.

Pull the updated image and recreate the application containers using Docker Compose.

This project demonstrates practical experience with version control, container image management, automated validation, remote deployment, and application lifecycle management.

3. Docker Networking & Reverse Proxy

Technologies: Docker Compose, Nginx, Linux networking

Configured separate Docker Compose projects.

Exposed applications through distinct host ports.

Practiced internal container-to-container communication.

Used Compose service names for backend discovery.

Investigated listening ports, routing, connectivity, and application availability.

4. Virtualization & Remote Administration

Technologies: Proxmox VE, Ubuntu, LXC, Tailscale, SSH

Manage virtual machines and Linux containers in Proxmox.

Run application workloads separately from the Plex LXC.

Use SSH for remote administration.

Use Tailscale for private connectivity to the homelab.

Practice Linux service management, system logs, memory and disk inspection, and network diagnostics.

🧰 Skills Practiced

Area

Current focus

Linux Administration

Services, processes, logs, storage, networking, troubleshooting

Networking

IP addressing, DNS, routing, ports, reverse proxies

Containers

Docker, Docker Compose, images, volumes, container networking

CI/CD

GitHub Actions, automated builds and tests, image publishing, deployment

Version Control

Git, branches, commits, merges, repository management

Remote Access

SSH, Tailscale, private connectivity

Cloud

Microsoft Azure fundamentals and administration

Infrastructure as Code

Terraform — planned

Configuration Management

Ansible — planned

Monitoring & Observability

Uptime Kuma, Prometheus, Grafana — planned

🛣️ Roadmap

Completed

Git and GitHub fundamentals

Docker and Docker Compose basics

Tailscale remote access and SSH

Docker networking

Homepage dashboard

Nginx reverse proxy

Containerized Python backend

GitHub Actions CI/CD pipeline

Automated Docker image publishing to GHCR

Remote application deployment

In Progress

Strengthen Linux administration and troubleshooting

Prepare for Microsoft Azure Administrator (AZ-104)

Improve infrastructure documentation

Planned

Uptime Kuma for service availability monitoring

Prometheus and Grafana for metrics and dashboards

Ansible for configuration management

Terraform for Infrastructure as Code

Kubernetes fundamentals and application deployment

Centralized logging and improved observability

Secrets management and infrastructure security improvements

📚 Learning Approach

Each project is an opportunity to understand not only how to deploy a service, but also how it works, how to troubleshoot it, and how to improve its reliability and maintainability.

The long-term goal is to evolve this homelab into a documented, automated, and observable infrastructure environment that reflects practical Infrastructure, Cloud, and DevOps engineering workflows.

