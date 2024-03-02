MERN Stack Deployment on Kubernetes
This repository contains the configuration files and instructions to deploy a MERN (MongoDB, Express.js, React.js, Node.js) stack application on Kubernetes. It uses Kubernetes to orchestrate the deployment of MongoDB, a Node.js backend, and a React.js frontend.

Prerequisites
Before you begin, make sure you have the following installed:

kubectl - Kubernetes command-line tool.
minikube - Local Kubernetes cluster tool.
Docker - For building Docker images.

Getting Started

1. Clone this repository:
    git clone https://github.com/juggepranay/Kubernetes.git
    cd your-repo
2. Start minikube:
    minikube start
3. Apply the Kubernetes configurations:
    kubectl apply -f mongo-config.yaml
    kubectl apply -f secret.yaml
    kubectl apply -f mongo-app.yaml
    kubectl apply -f web-app.yaml
4. Check the status of pods:
    kubectl get pods
5. Access the application:
    Get the IP of the minikube cluster:
    minikube ip

Open a web browser and go to http://MINIKUBE_IP:SERVICE_NODE_PORT to access the application.

Configuration
Secrets
The secret.yaml file contains the credentials for MongoDB. These are securely stored as Kubernetes secrets and accessed by the MongoDB deployment.

ConfigMap
The mongo-config.yaml file defines the MongoDB URL. This makes it easy to change the MongoDB URL without modifying the deployment configurations.

Deployments
mongo-app.yaml: Deploys MongoDB in a Kubernetes pod.
web-app.yaml: Deploys the Node.js backend and React.js frontend in a Kubernetes pod.
Services
The web-app.yaml file also creates a NodePort service to expose the application to external traffic. This allows you to access the MERN stack app from your local machine.


Cleaning Up

To delete all deployments and services:
    kubectl delete deployment --all
    kubectl delete service --all
    kubectl delete secret --all
    kubectl delete configmap --all

Additional Notes

    Ensure Docker is running to build the images for MongoDB and the MERN app.
    Customize the configurations in the YAML files according to your application needs.
    For production deployments, consider using more secure methods for storing secrets, such as Kubernetes Secrets with encryption providers.


