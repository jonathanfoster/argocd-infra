# Argo CD Infrastructure Demo

## Getting Started

### 1. Create a local Kubernetes cluster

```bash
kind create cluster --name=argocd-infra
```

### 2. Install Argo CD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 3. Access the Argo CD API Server

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

The API server can be accessed at <https://localhost:8080>.

### 4. Login to the Argo CD API Server

Get the admin password.

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```
