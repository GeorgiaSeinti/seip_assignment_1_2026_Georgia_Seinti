# Georgia Seinti - Software Engineering in Practice — Assignment 1 (2026)
## Advanced DevOps: Production-Grade CI/CD, External Configuration, and Orchestration

---

## 🎯 Objective

Purpose of this assignment was to build a complete, automated deployment pipeline for a cloud-native web application. I containerized the application, automated the delivery via GitHub Actions to the GitHub Container Registry (GHCR), and orchestrated the deployment inside a local Kubernetes (Minikube) cluster. 

This project helped me understand how modern cloud-native applications are deployed using industry-standard DevOps practices. By implementing CI/CD automation, declarative Kubernetes manifests, external configuration management and container orchestration, I replicated the same patterns used in enterprise production environments to ensure scalability, automation, security amd reliable application delivery.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following tools installed and configured on your local machine:
* **Git** & a verified **GitHub Account**
* **Docker Desktop** / Docker Engine (https://docs.docker.com/desktop/setup/install/windows-install/)
* **Minikube** & **kubectl** (https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download, https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)


---

## 1. Clone the Repository

To get started, clone the repository to your local machine using the following command

git clone https://github.com/GeorgiaSeinti/seip_assignment_1_2026_Georgia_Seinti.git
cd seip_assignment_1_2026_Georgia_Seinti

---

## 2. Start Minikube

Before deploying the application, start your local Kubernetes cluster using Minikube. To do that, use the following command

minikube start

---

## 3. Apply Kubernetes Manifests

All of the Kubernetes configuration files are located inside the k8s/ directory. In order to deploy the entire application, run the command:

kubectl apply -f k8s/

If everything works properly you should see in the terminal the following output:

configmap/echo-api-config created
deployment.apps/echo-api-deployment created
secret/echo-api-secret created
service/echo-api-service created

---

## 4. Verification of successful Deployment

To confirm that the Kubernetes deployment is running correctly, run the following command:

kubectl get all -n default

You should see 3 healthy running pods, the deployment status and the ClusterIP service


---

## 5. Port Forwarding

In order to map the internal ClusterIP service interface to your local machine network loopback run the following command

kubectl port-forward service/echo-api-service 3000:80

---

## 6. Application Verification

The application will be accessible at:

http://localhost:3000

Health endopoint:

http://localhost:3000/health