---
title: Deploy Spring to Kubernetes 
parent: Kubernetes
has_children: true
nav_order: 4
---

# Deploy to Kubernetes
## Using Commands
minikube start

minikube image load catalog-service:1.0

kubectl create deployment catalog-service --image=catalog-service:1.0

kubectl expose deployment catalog-service --name=catalog-service --port=8080 

kubectl port-forward service/catalog-service 8080:8080

**Stop and remove**

kubectl delete service catalog-service

kubectl delete deployment catalog-service

minikube stop