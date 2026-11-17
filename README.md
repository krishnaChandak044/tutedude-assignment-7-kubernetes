# Assignment 7 — Kubernetes with Minikube (Krishna)

**Repository:** https://github.com/krishnaChandak044/tutedude-assignment-7-kubernetes

The Flask and Express apps are in `app/`. `k8s/` contains Kubernetes Deployments/Services, probes, and a NodePort frontend (30080).

## Verified local deployment
Minikube ran locally with Docker driver. Both Deployments reached Ready; `kubectl get pods,svc -o wide` showed both pods Running and the frontend NodePort service. A port-forward request to Express `/api/health` returned the Flask backend JSON response. See `evidence/minikube-status.txt`, `evidence/api-response.json`, and `evidence/port-forward.log`. The cluster was stopped and its temporary local profile removed after evidence was captured to reclaim disk; the manifests and images can recreate it.

Recreate with:

```sh
minikube start --driver=docker --cpus=2 --memory=4096
docker build -t tutedude-flask-backend:local app/backend
docker build -t tutedude-node-frontend:local app/frontend
minikube image load tutedude-flask-backend:local
minikube image load tutedude-node-frontend:local
kubectl apply -k k8s
kubectl rollout status deployment/flask-backend
kubectl rollout status deployment/express-frontend
kubectl get pods,svc -o wide
minikube service frontend --url
```
