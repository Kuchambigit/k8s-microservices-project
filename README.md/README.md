# Kubernetes Microservices Project

## Overview
This project demonstrates a simple microservices architecture using Kubernetes.

- Frontend: NGINX (reverse proxy)
- Backend: hashicorp/http-echo
- Config: ConfigMap
- Exposure: NodePort Service

## Architecture
Client → NGINX → Backend Service → Backend Pod

## Setup

### 1. Deploy backend
kubectl apply -f k8s/backend-deployment.yaml
kubectl apply -f k8s/backend-service.yaml

### 2. Create ConfigMap
kubectl create configmap nginx-config --from-file=config/nginx.conf

### 3. Deploy frontend
kubectl apply -f k8s/frontend-deployment.yaml
kubectl apply -f k8s/frontend-service.yaml

### 4. Verify
kubectl get pods
kubectl get svc

### 5. Test
curl http://<NODE-IP>:<NODEPORT>
curl http://<NODE-IP>:<NODEPORT>/api

## Expected Output
Frontend:
Hello from frontend

Backend:
hello-from-backend
