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
```

| Layer | Tool / Technology | Role in Architecture |
|---|---|---|
| Frontend | HTML5, CSS3, Font Awesome | Modern dark UI, responsive grid/flexbox layout |
| Web Server | NGINX (alpine variant) | High-performance static web server |
| Containerization | Docker | Container image creation and local daemon management |
| Orchestration | Kubernetes (Minikube) | Deployment management, pods, and service routing |
| Cloud Hosting | AWS EC2 (Amazon Linux 2023) | Cloud virtual server hosting the cluster environment |
| Networking | EC2 Security Groups, kubectl | Port mapping and inbound traffic rule enforcement |
| Version Control | Git & GitHub | Code versioning and remote repository tracking |

---

## 🚀 Step-by-Step Deployment Guide

### 1. Build Container Image

Set the shell environment to Minikube's internal Docker daemon and build the production image:

```bash
eval $(minikube docker-env)
docker build -t netflix-clone:v4 .
```

### 2. Deploy & Service Configuration

Deploy the container to the cluster and expose it through a NodePort service:

```bash
# Create or update deployment image
kubectl set image deployment/netflix-deployment netflix-clone=netflix-clone:v4

# Verify deployment status
kubectl rollout status deployment/netflix-deployment
```

### 3. Traffic Routing & Background Binding

Expose the cluster service across all host network adapters in the background:

```bash
kubectl port-forward --address 0.0.0.0 service/netflix-service 30657:80 > /dev/null 2>&1 &
```

---

## 📂 Repository Layout

```text
netflix-clone-k8s/
├── index.html        # Responsive frontend markup
├── style.css         # Styling, overlays, and responsive breakpoints
├── Dockerfile        # Production multi-stage NGINX image build file
└── README.md         # Complete technical documentation
```

---

## 👤 Author

**GitHub:** [@samirmaji-tech](https://github.com/samirmaji-tech)
**Project Repository:** [samirmaji-tech/netflix-clone-k8s](https://github.com/samirmaji-tech/netflix-clone-k8s)
