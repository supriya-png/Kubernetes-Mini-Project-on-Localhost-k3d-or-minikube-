# Kubernetes Mini Project on Localhost

## Description

This project demonstrates deploying a Flask web application into a local Kubernetes cluster using k3d or minikube. It includes:

- Kubernetes Deployment and Service
- Ingress Controller with NGINX Ingress
- ConfigMaps and Secrets for configuration
- Horizontal Pod Autoscaler (optional)

## Technologies Used

- Kubernetes
- k3d or minikube
- Flask
- Docker
- ConfigMaps & Secrets
- NGINX Ingress Controller
- Horizontal Pod Autoscaler

## Folder Structure

k8s-mini-project/
├── app/
│ └── app.py
├── Dockerfile
├── k8s/
│ ├── deployment.yaml
│ ├── service.yaml
│ ├── ingress.yaml
│ ├── configmap.yaml
│ ├── secret.yaml
│ └── hpa.yaml
├── requirements.txt
└── README.md


## Setup Instructions

### Prerequisites

- Docker installed
- k3d or minikube installed
- kubectl installed

### Build Docker Image

For k3d:

```bash
k3d cluster create dev-cluster
docker build -t flask-app:latest .
k3d image import flask-app:latest -c dev-cluster
For minikube:


minikube start
eval $(minikube docker-env)
docker build -t flask-app:latest .
Apply Kubernetes Manifests
kubectl apply -f k8s/configmap.yaml
kubectl apply -f k8s/secret.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/ingress.yaml
kubectl apply -f k8s/hpa.yaml  # Optional
Ingress Access
For minikube:

minikube tunnel
Access app at:

arduino

http://localhost/
For k3d:

Ingress is automatically mapped to localhost if configured.

Horizontal Pod Autoscaler
Ensure metrics server is installed:

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
Check HPA status:

kubectl get hpa
Clean Up

kubectl delete -f k8s/
minikube stop
k3d cluster delete dev-cluster

Author
Supriya S P
