BhaveshPay — Kubernetes Deployment with LoadBalancer

A containerized web application deployed on Kubernetes using Amazon EC2, Minikube, Docker Hub, and a Kubernetes LoadBalancer Service.

Project Overview

This project demonstrates how to package a web application into a Docker image, publish it to Docker Hub, and deploy it on a Kubernetes cluster with multiple replicas and service-based traffic distribution.

Architecture

GitHub Repository → Docker Image → Docker Hub → Minikube on Amazon EC2 → Kubernetes Deployment → 3 Pods → LoadBalancer Service

Technologies Used

- Amazon EC2
- Amazon Linux 2023
- Docker
- Docker Hub
- Kubernetes
- Minikube
- kubectl
- YAML
- MobaXterm
- Git and GitHub

Implementation Steps

1. Launch an EC2 Instance

Launched an Amazon Linux EC2 instance and connected to it using MobaXterm SSH.

2. Install Container and Kubernetes Tools

Installed Docker, Minikube, and kubectl, then started the Docker service.

3. Build the Docker Image

Built the BhaveshPay web application image and tagged it for Docker Hub.

docker build -t natsucloud/bhaveshpay:latest .

4. Push the Image to Docker Hub

docker login -u natsucloud
docker push natsucloud/bhaveshpay:latest

5. Deploy the Application

Created a Kubernetes Deployment with three replicas using "deployment.yaml".

kubectl apply -f deployment.yaml
kubectl get deployments
kubectl get pods

6. Expose the Application

Created a Kubernetes Service of type "LoadBalancer" using "service.yaml".

kubectl apply -f service.yaml
kubectl get svc bhaveshpay-service

7. Verify the Deployment

kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get services

The three BhaveshPay Pods reached the Running state, and the Deployment showed 3/3 replicas ready.

Kubernetes Configuration

- Deployment: "bhaveshpay"
- Replicas: 3
- Container Image: "natsucloud/bhaveshpay:latest"
- Container Port: 80
- Service: "bhaveshpay-service"
- Service Type: LoadBalancer
- Service Port: 80

Repository Files

- "Dockerfile" — Builds the application image.
- "deployment.yaml" — Defines the Kubernetes Deployment and replicas.
- "service.yaml" — Exposes the application through a LoadBalancer Service.
- "index.html" — Application HTML.
- "styles.css" — Application styling.
- "app.js" — Application JavaScript.
- "50x.html" — Nginx error page.

Notes

This project uses Minikube on EC2 for learning and demonstration. The LoadBalancer Service was created successfully, but external browser access must be verified separately. A Minikube LoadBalancer is not automatically an AWS Elastic Load Balancer.

Learning Outcomes

- Containerizing a web application with Docker.
- Publishing Docker images to Docker Hub.
- Deploying applications using Kubernetes.
- Scaling an application to multiple replicas.
- Exposing applications through Kubernetes Services.
- Verifying Pods, Deployments, and Services.

Author

Bhavesh Dnyaneshwar Patil

GitHub: https://github.com/patilbhavesh1008-arch# Kubernetes-Bhaveh-Pay
