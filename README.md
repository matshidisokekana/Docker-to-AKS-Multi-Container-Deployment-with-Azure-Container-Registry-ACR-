
# 🚀 Deploying a Multi-Container Application to Azure Kubernetes Service (AKS) via Azure Portal

This project demonstrates how to deploy a **multi-container web application** to **Azure Kubernetes Service (AKS)** using the **Azure Portal**, without writing any infrastructure-as-code or using the command line to create the cluster.

It simulates a real-world cloud deployment by provisioning a Kubernetes cluster and running a containerized sample application consisting of several services:

* A **storefront (frontend)** web UI
* A **product service** for catalog data
* An **order service** for handling purchases
* A **RabbitMQ** message broker for backend communication

By completing this project, you will learn:

* How to create and configure an AKS cluster using the Azure web interface
* How to use **Azure Cloud Shell** and **`kubectl`** to interact with the Kubernetes cluster
* How to apply Kubernetes manifests to deploy and manage containerized workloads
* How to expose a service to the internet using a **LoadBalancer**
* How to verify that a multi-container app is successfully running in the cloud

This project is ideal for anyone starting out with Kubernetes and Azure, providing a hands-on introduction to managing cloud-native applications in a real production-like environment.

---

## 📌 Project Objectives

- Provision a Kubernetes cluster using Azure Portal
- Connect to the AKS cluster using Azure Cloud Shell
- Deploy a sample multi-container app (storefront, product service, order service, RabbitMQ)
- Expose the app publicly using a Kubernetes LoadBalancer
- Validate deployment via a public IP

---

## 🛠️ Tools & Technologies

- Azure Kubernetes Service (AKS)
- Azure Portal
- Azure CLI in Cloud Shell
- Kubernetes
- Docker (pre-built images from Microsoft)

---

## ⚙️ Deployment Steps

### 1. Create AKS Cluster via Portal

- Go to the Azure Portal → Kubernetes Services → Create
- Use default settings (e.g., Dev/Test, single node pool)
- Select **Region** (e.g., East US) and create a **new resource group**
- Cluster preset: **Dev/Test**
- Click **Review + Create**, then **Create**

### 2. Connect to the Cluster

Once provisioned:
- Open **Azure Cloud Shell** and run:
```bash
az aks get-credentials --resource-group <your-rg> --name <your-cluster-name>
kubectl get nodes
````

### 3. Deploy the Sample App

Download and apply the manifest:

```bash
wget https://raw.githubusercontent.com/Azure/aks-store-demo/main/aks.yaml
kubectl apply -f aks.yaml
```

### 4. Verify the App

Watch for external IP:

```bash
kubectl get service store-front --watch
```

Once the IP appears, open it in a browser to view the deployed multi-container app.

---

## 📂 Project Structure

This project uses a single Kubernetes manifest (`aks.yaml`) that includes:

* **store-front** (frontend UI)
* **product service**
* **order service**
* **RabbitMQ (message queue)**

---


## 🔒 Security & Cleanup

To avoid charges, delete the resource group when done:

```bash
az group delete --name <your-resource-group-name> --yes --no-wait
```
---

## 🌐 Project Purpose and Importance

### 🔍 Why This Project Matters

Kubernetes has become the industry standard for managing containerized applications at scale. Microsoft Azure Kubernetes Service (AKS) offers a **fully managed Kubernetes** solution that simplifies deploying, managing, and operating Kubernetes clusters in the cloud.

By completing this project:

* I **gained practical experience** deploying infrastructure in Azure using the Portal interface.
* I developed a deeper understanding of **cloud-native workloads**, container orchestration, and **DevOps practices**.
* It demonstrates my ability to set up **scalable, resilient environments** ready for real-world workloads and microservices.

---

## ✅ Why Do We Need AKS?

* **Simplified Management**: Azure handles the Kubernetes control plane, reducing operational overhead.
* **Scalability**: AKS can scale your applications automatically based on load or predefined policies.
* **Cost Efficiency**: Only pay for agent nodes, not the control plane.
* **Security & Integration**: Built-in Azure AD support, RBAC, and integration with Azure Monitor and Defender for Cloud.
* **DevOps & CI/CD**: Easily connects with Azure DevOps, GitHub Actions, and Helm for automated deployments.

Use cases:

* Hosting containerized web apps and microservices
* Big Data and ML workloads
* Development and test environments
* Event-driven applications (using message queues, etc.)

---

## 🚧 Challenges Faced

### 1. **Resource Group and Region Selection**

* Choosing the correct Azure region that supports all AKS features was crucial but confusing at first.

### 2. **Node Pool Configuration**

* Understanding VM sizing (Standard\_DS2\_v2, Standard\_B2s, etc.) and the cost implications took time.
* Learning how many nodes to deploy for performance testing was a bit of trial and error.

### 3. **Networking Options**

* Deciding between **basic networking** and **advanced (Azure CNI)** required research to understand the implications for IP ranges and connectivity.

### 4. **Authentication Setup**

* Setting up Azure AD integration and Service Principals was a bit tricky without CLI commands, especially from the Portal.

### 5. **Cluster Validation**

* It took a few attempts to properly configure `kubectl` via Azure CLI (`az aks get-credentials`) and test that the cluster was reachable.

### 6. **Cost Management**

* Since this was a test project, I had to be careful to delete the resources immediately to avoid charges.

---
## ✅ What I Learned

* How to provision an AKS cluster entirely through Azure Portal
* Using `kubectl` to manage deployments in Azure Cloud Shell
* Understanding basic Kubernetes concepts: pods, services, LoadBalancer
* Deploying and exposing a multi-container app in a real cloud environment

---

## 🎯 Key Takeaways

* Hands-on deployment helped bridge theory with practice.
* Realized the **power and flexibility of AKS**, but also the importance of **planning and security** in cloud environments.
* Highlighted areas to improve: automation (Bicep/Terraform), monitoring (Azure Monitor), and secure networking.

---
## 🙋🏽‍♂️ Author

**Matshidiso M. Kekana**
[GitHub](https://github.com/yourusername) | [LinkedIn](https://linkedin.com/in/yourprofile)




