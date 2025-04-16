# Minikube with Docker☸️

<p align="center">
  <img src="https://raw.githubusercontent.com/TarakKatoch/My-Docker-Dockyard/54505203108590859cc273cd9a1c18bb9f018e76/Minikube%20with%20Docker%20on%20Windows/assets/logo.png" alt="Minikube Logo" width="200" />
</p>

## What is Minikube? 

**Minikube** is a tool that helps you run a local Kubernetes cluster on your machine. It's perfect for developers who want to experiment with Kubernetes without setting up a large cloud infrastructure. Minikube provides a simple way to start a Kubernetes cluster on a local machine, and it works with various drivers like Docker, VirtualBox, and Hyper-V.

Minikube makes Kubernetes accessible for local development, testing, and experimentation. It simplifies the process of deploying and managing Kubernetes clusters locally without the need for extensive resources.

---

## What is Kubernetes? ☸️

**Kubernetes** is an open-source platform for automating the deployment, scaling, and management of containerized applications. It orchestrates and manages containers (such as those created with Docker) to ensure that applications run reliably and efficiently, whether in a development, test, or production environment.

Kubernetes allows you to:
- Deploy applications in containers across clusters.
- Scale applications up or down with ease.
- Manage containerized workloads with minimal effort.
- Ensure high availability, load balancing, and fault tolerance for your applications.

By using Kubernetes, developers can focus on writing code and let Kubernetes manage the complexity of application deployment and scaling.

---

## ✅ Step 1: Install Required Tools

Before starting, ensure you have the necessary software installed.

### 1. Install Docker Desktop 🐋

Minikube can run Kubernetes inside a Docker container, so install Docker Desktop:

- [Download and install Docker Desktop](https://www.docker.com/products/docker-desktop/)

**During installation:**
- Make sure WSL 2 backend is enabled (recommended). ⚙️
- If you have Windows Pro/Enterprise, enable Hyper-V (Docker will handle this). 🔧

### 2. Install Minikube 📦

To download and install Minikube, open CMD or PowerShell as Administrator and run the following command:
```bash
choco install minikube
```
![image](https://github.com/user-attachments/assets/8ca2f6e6-9ce2-42b6-806e-087455b65152)

If you don't have Chocolatey, [install Minikube manually](https://minikube.sigs.k8s.io/docs/start/).

### 3. Install kubectl

```bash
choco install kubernetes-cli
```
![image](https://github.com/user-attachments/assets/45d24724-3789-49d4-93dc-88919ff6be82)

Verify installation:
```bash
kubectl version --client
```
![image](https://github.com/user-attachments/assets/1d4d125e-6273-4698-984c-1e6840e261d8)

---

## ✅ Step 2: Start Minikube with Docker Driver 🐳

Now, start Minikube using Docker as the driver. Ensure that your Docker Engine (Docker Desktop) is running in the background.

### 1. Start Minikube
```bash
minikube start --driver=docker
```
This initializes a Kubernetes cluster inside a Docker container instead of a virtual machine.
![image](https://github.com/user-attachments/assets/2a240e04-b5de-4890-835e-9e1aef0ce460)

Check the status:
```bash
minikube status
```
![image](https://github.com/user-attachments/assets/6c5d2106-ba31-4b93-b515-d657e619aecf)

---

## ✅ Step 3: Deploy an Application 🚀

Deploy a simple application (nginx).

### 1. Create an Nginx Deployment
```bash
kubectl create deployment nginx --image=nginx
```

### 2. Expose the Deployment 🔓
```bash
kubectl expose deployment nginx --type=NodePort --port=80
```

### 3. Get the Service URL 🔗
```bash
minikube service nginx --url
```
Open the URL in your browser to see the running nginx web server. 🌐
![image](https://github.com/user-attachments/assets/affc039c-4245-46e2-91a2-85dbb312baac)

---

## ✅ Step 4: Manage Kubernetes Cluster

### 1. Check Running Pods 📋
```bash
kubectl get pods
```
![image](https://github.com/user-attachments/assets/d8f0e9f3-4f6d-4550-a1d3-d71adccc370c)
![image](https://github.com/user-attachments/assets/af5e020b-8526-4b1d-9fec-b764d1ea30cb)

### 2. Scale the Deployment 📏
Scale to 3 replicas:
```bash
kubectl scale deployment nginx --replicas=3
```
Check pods again:
```bash
kubectl get pods
```
![image](https://github.com/user-attachments/assets/c9e09a5c-333b-4931-8d1d-ff95eff59a4c)

### 3. Delete the Deployment 🧹
```bash
kubectl delete service nginx
kubectl delete deployment nginx
```
![image](https://github.com/user-attachments/assets/f92aae1a-b4a1-456d-ab8c-83aa5e78c1aa)

---

## ✅ Step 5: Stop and Delete Minikube 🗑️

### 1. Stop Minikube
```bash
minikube stop
```

### 2. Delete the Cluster 
```bash
minikube delete
```
This removes all Kubernetes resources.
![image](https://github.com/user-attachments/assets/25b2a54f-bf56-463d-8784-0642786aaa01)

---

## 🎯 Conclusion

By using Minikube with Docker, you can run Kubernetes locally without needing Hyper-V or VirtualBox. Docker provides an easy way to manage your cluster and experiment with Kubernetes.

🚀😊


