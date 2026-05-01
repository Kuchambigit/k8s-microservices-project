# 🚀 Kubernetes Microservices App

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.29-blue)
![NGINX](https://img.shields.io/badge/NGINX-Reverse%20Proxy-green)
![Status](https://img.shields.io/badge/Status-Working-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Project Overview

This project demonstrates a **microservices architecture** deployed on Kubernetes.

It includes:
- 🔹 Frontend UI (NGINX + HTML + JavaScript)
- 🔹 Backend API service
- 🔹 NGINX reverse proxy (via ConfigMap)
- 🔹 Kubernetes Deployments, Services, and Ingress

---

## 🏗️ Architecture Diagram

    +------------------+
    |   Browser        |
    | myapp.local      |
    +--------+---------+
             |
             ↓
    +------------------+
    |   Ingress        |
    +--------+---------+
             |
             ↓
    +------------------+
    |  Frontend (NGINX)|
    |  Serves UI       |
    +--------+---------+
             |
         /api request
             ↓
    +------------------+
    | Backend Service  |
    +--------+---------+
             ↓
    +------------------+
    | Backend Pod      |
    | Returns response |
    +------------------+

---

## ⚙️ Tech Stack

- Kubernetes (k3s)
- NGINX (reverse proxy)
- HTML / JavaScript (frontend)
- Docker containers
- GitHub

---

## 📁 Project Structure


k8s-microservices-project/
│
├── config/
│ ├── nginx.conf
│ └── index.html
│
├── k8s/
│ ├── backend-deployment.yaml
│ ├── backend-service.yaml
│ ├── frontend-deployment.yaml
│ └── frontend-service.yaml
│
├── ingress.yaml
└── README.md


---

## ▶️ How to Run

### 1️⃣ Deploy all resources
```bash
kubectl apply -f k8s/
kubectl apply -f ingress.yaml
2️⃣ Restart frontend (after config changes)
kubectl rollout restart deployment frontend
3️⃣ Access the app
http://myapp.local
🧪 Testing
Test frontend
curl -H "Host: myapp.local" http://<NODE-IP>
Test backend
curl -H "Host: myapp.local" http://<NODE-IP>/api

Expected output:

hello-from-backend
✅ Features
✔️ Frontend UI served via NGINX
✔️ Backend API accessible via /api
✔️ Reverse proxy using ConfigMap
✔️ Ingress routing using hostname
✔️ Dynamic API call using JavaScript (fetch())
📸 Demo

Frontend UI:

Displays: Hello from Frontend UI
Button triggers API call
Returns: hello-from-backend
🔧 Key Kubernetes Concepts
ConfigMap
Injects NGINX config + HTML into container
Service
Exposes pods internally (ClusterIP / NodePort)
Ingress
Routes external traffic using host-based routing
Deployment
Manages pod lifecycle and scaling
🚀 Future Improvements
🔹 Add CI/CD pipeline (GitHub Actions / Jenkins)
🔹 Deploy to AWS EKS
🔹 Add monitoring (Prometheus + Grafana)
🔹 Implement autoscaling (HPA)
🔹 Add health checks (liveness & readiness probes)
👨‍💻 Author

Kuchambi Atud
