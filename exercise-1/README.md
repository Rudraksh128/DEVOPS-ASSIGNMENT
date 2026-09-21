# Exercise 1 — Kubernetes Getting Started

## Final Result

The Nginx application was successfully deployed as a Kubernetes Pod using **Minikube** and accessed through a **NodePort Kubernetes Service**.

The application was verified by opening the Nginx welcome page in the browser through the Minikube service.

---

## Technologies Used

* Kubernetes
* Minikube
* Docker
* kubectl
* Nginx
* Windows PowerShell

---

## Steps Performed

### 1. Start Minikube

A local Kubernetes cluster was started using Minikube with the Docker driver.

```powershell
minikube start --driver=docker
```

The cluster status was verified using:

```powershell
minikube status
```

---

### 2. Deploy Nginx Pod

An Nginx container was deployed as a Kubernetes Pod.

```powershell
kubectl run hello-k8s --image=nginx --port=80
```

The Pod was verified using:

```powershell
kubectl get pods
```

The Pod successfully reached the `Running` state:

```text
NAME        READY   STATUS    RESTARTS   AGE
hello-k8s   1/1     Running   0          ...
```

---

### 3. Expose the Pod as a Service

The Nginx Pod was exposed using a Kubernetes NodePort Service.

```powershell
kubectl expose pod hello-k8s --type=NodePort --port=80
```

The Service was verified using:

```powershell
kubectl get services
```

---

### 4. Access the Nginx Application

The Nginx application was opened through the Minikube Service command:

```powershell
minikube service hello-k8s
```

This opened the Nginx welcome page in the browser.

---

## Kubernetes Architecture

```text
                    Browser
                       │
                       ▼
              NodePort Service
                hello-k8s
                       │
                       ▼
              Kubernetes Pod
                 hello-k8s
                       │
                       ▼
              Nginx Container
                       │
                       ▼
                   Port 80
```

---

## Commands Executed

The following commands were executed in Windows PowerShell to create the Minikube cluster, deploy the Nginx Pod, verify its status, expose it as a Service, and access the application.

```powershell
# Start Minikube
minikube start --driver=docker

# Check Minikube status
minikube status

# Deploy Nginx Pod
kubectl run hello-k8s --image=nginx --port=80

# Verify Pod
kubectl get pods

# Expose Pod as NodePort Service
kubectl expose pod hello-k8s --type=NodePort --port=80

# Verify Service
kubectl get services

# Open the application
minikube service hello-k8s
```

---

## Final Outcome

The exercise successfully demonstrated the basic Kubernetes deployment workflow:

**Minikube Cluster → Pod → Nginx Container → Service → Browser**

The Nginx application was successfully deployed and accessed through Kubernetes.
