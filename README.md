## 🚀 Automating Grafana Dashboard Provisioning in Minikube

This project demonstrates how to deploy [Grafana](https://grafana.com/) into a local Kubernetes cluster using [Minikube](https://minikube.sigs.k8s.io/). The main goal of this project is to automate the provisioning of Grafana dashboards, allowing for easy and reproducible deployment of pre-configured dashboards into Grafana instances running in Kubernetes.

### ✅ Prerequisites

- Minikube installed and running (`minikube start`)
- `kubectl` installed and configured to use Minikube
- This repository cloned locally

---

### 🛠️ Deployment Steps

1. **Apply the deployments:**

   ```bash
   kubectl apply -f k8s/grafana/deployment.yml
   kubectl apply -f k8s/timescaledb/deployment.yml
   ```

2. **Check that the Pods are running:**

    ```bash
    kubectl get pods
    ```

3. **Apply the services:**

    ```bash
    kubectl apply -f k8s/grafana/service.yml
    kubectl apply -f k8s/timescaledb/service.yml
    ```

4. **Access Grafana in your browser:**

    ```bash
    minikube service grafana
    ```

### 🔐 Access Grafana and Login Credentials

After deploying Grafana, you can access it by running the following command to open it in your default web browser:
    ```bash
    minikube service grafana
    ```

This will open Grafana at the Minikube service URL, typically at `http://<minikube-ip>:<node-port>`. If everything is set up correctly, Grafana will be accessible. The first time you log in, you will be prompted to use the default credentials:

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