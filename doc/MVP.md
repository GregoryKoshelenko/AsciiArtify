# MVP Demo: 🚀 Deploying and Auto-Syncing an Application with ArgoCD 🎯

## Goal 🎯

Demonstrate how ArgoCD can automatically deploy and synchronize the [go-demo-app](https://github.com/den-vasyliev/go-demo-app) from a Git repository to your Kubernetes cluster.

---

## Step 1. Prepare ArgoCD UI 🖥️

- Ensure ArgoCD is running and accessible (see PoC instructions).
- Log in to the ArgoCD UI at http://localhost:8080 with your admin credentials.
  
See the [POC.md](POC.md) for setup instructions if needed.
---

## Step 2. Create an ArgoCD Application 🛠️

Use the ArgoCD UI:
- Go to "Applications" → "NEW APP" ➕
- Fill in the fields as above (repo URL, path: k8s, destination: default namespace)
- Repository URL: https://github.com/den-vasyliev/go-demo-app
- Path: helm
- Current cluster: `kubernetes.default.svc`
- Namespace: `demo`
- Create ✅
- SYNC 🔄
---

## Step 3. Verify Deployment 🔍

- In the ArgoCD UI, you should see the `demo` application.
- Status should be "Synced" and "Healthy". 🟢
- If you have Degraded status, check the logs for errors. ⚠️

---

## Video Demo (Optional) 🎥
[Watch the demo video](https://jam.dev/c/2eb196d2-790e-4373-92db-a0e8ca13fafa)

