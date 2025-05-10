## 🚀 Deploying Grafana to Minikube

This project contains a simple setup for deploying [Grafana](https://grafana.com/) into a local Kubernetes cluster using [Minikube](https://minikube.sigs.k8s.io/).

### ✅ Prerequisites

- Minikube installed and running (`minikube start`)
- `kubectl` installed and configured to use Minikube
- This repository cloned locally

---

### 🛠️ Deployment Steps

1. **Apply the deployment:**

   ```bash
   kubectl apply -f k8s/grafana/deployment.yml
   ```

2. **Check that the Grafana Pod is running:**

    ```bash
    kubectl get pods
    ```

3. **Apply the service:**

    ```bash
    kubectl apply -f k8s/grafana/service.yml
    ```

4. **Access Grafana in your browser:**

    ```bash
    minikube service grafana
    ```