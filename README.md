# Assignment 7 — Kubernetes with Minikube (Krishna)

**Repository:** https://github.com/krishnaChandak044/tutedude-assignment-7-kubernetes

`app/` contains the Flask and Express containers from Assignment 5. `k8s/` contains independent Kubernetes Deployments and Services, probes, and a NodePort frontend (30080). Run on a machine with Minikube and kubectl:

```sh
minikube start
docker build -t tutedude-flask-backend:local app/backend
docker build -t tutedude-node-frontend:local app/frontend
minikube image load tutedude-flask-backend:local
minikube image load tutedude-node-frontend:local
kubectl apply -k k8s
kubectl rollout status deployment/flask-backend
kubectl rollout status deployment/express-frontend
kubectl get pods,svc
minikube service frontend --url
```

The local machine has Docker but not Minikube, so the manifests/images are prepared but a Minikube cluster run was not possible here. Do not mistake Docker Compose screenshots from Assignment 5 for Kubernetes pod/service evidence.
