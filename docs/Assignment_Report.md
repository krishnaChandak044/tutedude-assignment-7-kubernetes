# Assignment 7 local Kubernetes report

Deployed the previous assignment’s Flask backend and Express frontend locally in Minikube using Docker-built images. `k8s/backend.yaml` and `k8s/frontend.yaml` define a Deployment and Service for each application, plus readiness/liveness probes. The frontend service is NodePort 30080; the backend is ClusterIP on 5000.

Evidence: both pods reached Running/1-of-1 Ready, `kubectl get pods,svc -o wide` captured both Services, and an HTTP request to the frontend’s `/api/health` returned the Flask backend response. Evidence files are in `../evidence`. The cluster profile was stopped then removed after capturing evidence to free local disk; `README.md` has recreation commands.
