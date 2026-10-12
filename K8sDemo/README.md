## Description
Demo project for Kubernetes (K8s). It includes sample configurations for deploying a simple application on a local Kubernetes cluster using Minikube. The project demonstrates the use of Kubernetes manifests, services, and deployments.

- ## Structure
The project is organized as follows:
```
├── mongo-config.yaml  # MongoDB configuration
├── mongo-secret.yaml  # secrets for MongoDB credentials
├── mongo.yaml                # Template for the mongoDB Pod
│   ├── Deployment configuration
│   └── Service configuration
├── webapp.yaml    # Template configuration for the webapp Pod
│   ├── Deployment configuration
│   └── Service configuration
```
- ## How to run it
1. Install Minikube, kubectl and docker desktop on your local machine.
2. Open a terminal and initialize docker and minikube.
```
docker start
minikube start
```
3. Make docker the default driver for minikube.:
```
minikube config set driver docker
```
4. Check that the minikube's default cluster and node are running:
```
minikube kubectl get nodes
```
5. Apply the MongoDB configuration and secret:
```
kubectl apply -f mongo-config.yaml
kubectl apply -f mongo-secret.yaml
```
6. Deploy the MongoDB pod and service:
```
kubectl apply -f mongo.yaml
```
7. Deploy the web application pod and service:
```
kubectl apply -f webapp.yaml
```
8. Check the status of the pods and services:
```
kubectl get all
```
9. Get the minikube IP address and the webapp service port:
```
minikube ip 
kubectl get svc webapp-service
```
10. Open the web application in your browser:
```
http://<minikube-ip>:<webapp-service-nodeport>
```