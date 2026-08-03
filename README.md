# 🎬 Netflix Clone – Deployed on Kubernetes (Minikube) & AWS EC2

A responsive Netflix landing page clone containerized with NGINX, orchestrated using Kubernetes (Minikube), and hosted on an AWS EC2 instance.

---

## 📌 Project Overview

This project demonstrates an end-to-end cloud and DevOps workflow, covering application development, containerization, container orchestration, traffic routing, and version-controlled deployment on cloud infrastructure.

### Key Features
* **Pixel-Perfect UI:** Features the updated Netflix India landing page with movie poster background collage, localized language selector, and curved border accents.
* **Lightweight Web Server:** Served via `nginx:alpine` for minimal memory footprint and fast startup times.
* **Kubernetes Orchestration:** Container managed via Kubernetes Deployment and exposed via NodePort service architecture.
* **AWS Hosted:** Running on Amazon Linux 2023 EC2 infrastructure with configured security groups for public access.

---

## 🛠️ Tech Stack & Tools

| Layer | Technology Used |
| :--- | :--- |
| **Frontend** | HTML5, CSS3, Font Awesome |
| **Web Server** | NGINX (`alpine` base) |
| **Containerization** | Docker |
| **Orchestration** | Kubernetes (Minikube) |
| **Cloud Infrastructure** | AWS EC2 (Amazon Linux 2023) |
| **Version Control** | Git & GitHub |

---

## 🚀 Architecture & Deployment Steps

### 1. Web Application Development
Static assets (`index.html` and `style.css`) were crafted to match Netflix's latest design specifications, including flexible hero layouts, custom responsive breakpoints, and dark mode overlays.

### 2. Docker Containerization
Created a multi-stage/alpine `Dockerfile` to serve static assets efficiently:
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
COPY style.css /usr/share/nginx/html/style.css
EXPOSE 80
