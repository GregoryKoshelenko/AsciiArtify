# POC: Deploying ArgoCD on a Local Kubernetes Cluster (k3d)
<p align="center">
  <img src="argocd.png" alt="GitOps system ArgoCD">
</p>

## Description

This PoC demonstrates the deployment of the GitOps system ArgoCD in a local Kubernetes cluster created with k3d. After following this guide, the team will have access to the ArgoCD graphical interface for further MVP development.

---

## Step 1. Create a Local Kubernetes Cluster with k3d

```bash
# Install k3d (Linux)
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

# Create a cluster with port 8082 exposed for service access
k3d cluster create argocd-demo --port 8082:80@loadbalancer --kubeconfig-update-default=true

# Check cluster status
kubectl get nodes
```

---

## Step 2. Install ArgoCD

```bash
# Create a namespace for ArgoCD
kubectl create namespace argocd

# Install ArgoCD (Stable release)
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Check pod status
kubectl get pods -n argocd
```

---

## Step 3. Access the ArgoCD UI

```bash
# Forward port to access ArgoCD UI (localhost:8080)
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

- The web interface will be available at: http://localhost:8080

### Get the Admin Password

```bash
# Get the initial password (argocd-server pod name)
kubectl get pods -n argocd

# Get the password (from the argocd-initial-admin-secret)
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

- Username: admin
- Password: (value from the previous command)

---

## Step 4. Demo Instructions for Logging into ArgoCD

1. Open your browser and go to http://localhost:8080
2. Enter username: `admin` and the password obtained in the previous step
3. You will see the ArgoCD graphical interface

![ArgoCD UI](https://argo-cd.readthedocs.io/en/stable/assets/argo-ui.png)

---

## Additional

- Official documentation: [ArgoCD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started/)
- To stop the cluster:

```bash
k3d cluster delete argocd-demo
```
