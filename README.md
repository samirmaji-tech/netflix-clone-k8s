# 🎬 Netflix Clone – Deployed on Kubernetes (Minikube) & AWS EC2

A fully responsive, containerized Netflix landing page clone orchestrated using **Kubernetes (Minikube)** on an **AWS EC2** instance running Amazon Linux 2023.

---

## 📌 Executive Summary

This project demonstrates an end-to-end cloud infrastructure and DevOps workflow—from initial frontend development to Docker containerization, Kubernetes orchestration, host-level network bridging, and public exposure via AWS Security Groups.

### Key Highlights
* **Optimized Image Footprint:** Built on lightweight `nginx:alpine` for minimal resource usage and rapid container startup.
* **Kubernetes Orchestration:** Utilized Kubernetes Deployments and NodePort Services to handle pod lifecycles and application exposure.
* **Zero-Downtime Rolling Updates:** Executed rolling upgrades across multiple versions (`v1` through `v4`) using `kubectl set image`.
* **Public Cloud Edge Routing:** Configured `kubectl port-forward` across all host interfaces (`0.0.0.0`) paired with AWS EC2 Inbound Rules for global access.

---

## 🛠️ Tech Stack & Architecture

```text
[ Client Browser ] 
        │
        ▼  (Public IP : Port 30657 via AWS Security Group)
[ AWS EC2 Instance (Amazon Linux 2023) ]
        │
        ▼  (Port Forwarding on 0.0.0.0 Interface)
[ Kubernetes Cluster (Minikube) ]
        │
        ▼  (NodePort Service Target Port 80)
[ Pod: netflix-deployment (NGINX:Alpine v4) ]
