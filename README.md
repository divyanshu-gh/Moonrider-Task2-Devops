

This repository contains the **Product Catalog Microservice** built using Spring Boot and deployed on Kubernetes using Minikube with CI/CD integration.

---

## 🚀 Tech Stack
- Java Spring Boot
- Docker
- Kubernetes (Minikube)
- GitHub Actions

---

## ✅ Step-by-Step Execution Guide

### ✅ PHASE 1: Start Minikube and Enable Ingress
```bash
minikube start --driver=docker
minikube addons enable ingress
```

📸 Screenshot:  
![Minikube Ingress Enabled](https://github.com/divyanshu-gh/Moonrider-Task2-Devops/blob/main/successfully%20starting%20Minikube%20and%20enabling%20the%20Ingress%20addon..jpg)

---

### ✅ PHASE 2: Docker Image Build (All Versions)
```bash
docker build -t hungrykoala1/product:v1 .
docker build -t hungrykoala1/product:v1.1 .
docker build -t hungrykoala1/product:v2 .
```

---

### ✅ PHASE 3: Kubernetes Deployment

#### 1. Create Namespaces
```bash
kubectl create namespace v1
kubectl create namespace v11
kubectl create namespace v2
```

#### 2. Apply Deployment YAMLs
```bash
kubectl apply -f k8s/v1-deployment.yaml -n v1
kubectl apply -f k8s/v1.1-deployment.yaml -n v11
kubectl apply -f k8s/v2-deployment.yaml -n v2
```

#### 3. Apply Ingress
```bash
kubectl apply -f k8s/ingress.yaml
```

---

### ✅ PHASE 4: Access the Application

Check Minikube IP:
```bash
minikube ip
```

Test in browser:
```
http://<minikube-ip>/v1/health
http://<minikube-ip>/v1.1/products/search?q=tv
http://<minikube-ip>/v2/products/search?q=tv
```

---

### ✅ PHASE 5: CI/CD with GitHub Actions

1. Push changes to GitHub repository  
2. Navigate to `Actions` tab in GitHub  
3. Monitor the CI/CD pipeline:
   - Build  
   - Test  
   - Deploy  



