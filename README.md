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

### 🔐 Default Login Credentials

When Grafana starts for the first time and no credentials are configured, it uses the following default credentials:

- **Username:** `admin`  
- **Password:** `admin`

You will be prompted to change the password upon first login.  
To override these credentials, you can set the environment variables `GF_SECURITY_ADMIN_USER` and `GF_SECURITY_ADMIN_PASSWORD` in your deployment configuration `k8s\grafana\deployment.yml`.

### 🌐 Connecting Grafana to TimescaleDB

After deploying both Grafana and TimescaleDB, you can add TimescaleDB as a data source in Grafana.

1. Open Grafana in your browser:
   ```bash
   minikube service grafana
   ```

2. Go to **Connections** → **Data sources** → **Add new data source**, and select **PostgreSQL**.

3. Fill in the connection details:

    Host: `timescaledb:5432`

    Database: `timescaledb`

    User: `user`

    Password: `password`

    SSL mode: `disable`

4. Click Save & Test to verify the connection.